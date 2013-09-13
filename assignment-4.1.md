class Bootstrap {

    private $_url = null;
    private $_controller = null;
    
    private $_controllerPath = 'controllers/'; // Always include trailing slash
    private $_modelPath = 'models/'; // Always include trailing slash
    private $_errorFile = 'error.php';
    private $_defaultFile = 'index.php';
    
    /**
* Starts the Bootstrap
*
* @return boolean
*/
    public function __construct()
    {
        // Sets the protected $_url
        $this->_getUrl();

        // Load the default controller if no URL is set
        // eg: Visit http://localhost it loads Default Controller
        if (empty($this->_url[0])) {
            $this->_loadDefaultController();
            return false;
        }

        $this->_loadExistingController();
        $this->_callControllerMethod();
    }
    
    /**
* (Optional) Set a custom path to controllers
* @param string $path
*/
    public function setControllerPath($path)
    {
        $this->_controllerPath = trim($path, '/') . '/';
    }
    
    /**
* (Optional) Set a custom path to models
* @param string $path
*/
    public function setModelPath($path)
    {
        $this->_modelPath = trim($path, '/') . '/';
    }
    
    /**
* (Optional) Set a custom path to the error file
* @param string $path Use the file name of your controller, eg: error.php
*/
    public function setErrorFile($path)
    {
        $this->_errorFile = trim($path, '/');
    }
    
    /**
* (Optional) Set a custom path to the error file
* @param string $path Use the file name of your controller, eg: index.php
*/
    public function setDefaultFile($path)
    {
        $this->_defaultFile = trim($path, '/');
    }
    
    /**
* Fetches the $_GET from 'url'
*/
    private function _getUrl()
    {
        $url = isset($_GET['url']) ? $_GET['url'] : null;
        $url = rtrim($url, '/');
        $url = filter_var($url, FILTER_SANITIZE_URL);
        $this->_url = explode('/', $url);
    }
    
    /**
* This loads if there is no GET parameter passed
*/
    private function _loadDefaultController()
    {

        // write URL cookie
        $this->writeUrlCookie($this->_url);

        require $this->_controllerPath . $this->_defaultFile;
        $this->_controller = new Index();
        $this->_controller->index();
    }
    
    /**
* Load an existing controller if there IS a GET parameter passed
*
* @return boolean|string
*/

// Variable names could be more descriptive
//