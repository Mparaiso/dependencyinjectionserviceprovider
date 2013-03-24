Dependency injection service provider for Silex
===============================================

author: MParaiso
contact: mparaiso@online.fr
status: Work in Progress

### Configuration

        use Mparaiso\Provider\DependencyInjectionServiceProvider;

        $app->register(new DependencyInjectionServiceProvider,array(
           /* cache configuration (path and a cache class name */
           "di.cache"=>array("path"=>__DIR__."/../cache/","class"=>"MyCacheClass"),
           /* external variables ( db config , environment variables .... */
           "di.params"=>array(
               "app.root_dir"=>__DIR__,
               "app.debug"=>$app["debug"],
               "app.host"=>getenv("SYMFONY__SHORTEN__HOST"),
               "app.driver"=>"pdo_mysql",
               "app.user"=>getenv("SYMFONY__SHORTEN__USER"),
               "app.password"=>getenv("SYMFONY__SHORTEN__PASSWORD"),
               "app.dbname"=>getenv("SYMFONY__SHORTEN__DBNAME"),
               "app.port"=>getenv("SYMFONY__SHORTEN__PORT"),
               ),
           /* loader type (yaml,annotaions,xml) and file path */
           "di.loader.options"=>array(
               "type"=>"yaml",
               "path"=>__DIR__."/Shorten/Resources/services/config.yml",
               )
           )
        );

### Usage

        $app["di"]->get("myservice");

