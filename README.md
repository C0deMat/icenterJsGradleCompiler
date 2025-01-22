



# Js Gradle Compiler :zap:

A simple Js compiler for gradle (tested only on Gradle 6.0+, but it should work with all versions). Given a folder containing .js files, the plugin will compile using Google closure compiler and minify them.



## Instructions :pencil:

#### Import the plugin
Place one of these code snippets in build.gradle: 
```groovy
plugins {
  id "io.github.C0deMat.icenterjsgradlecompiler" version "0.4.0"
}
```

or using legacy plugin app:
```groovy
buildscript {
  repositories {
    maven {
      url "https://plugins.gradle.org/m2/"
    }
  }
  dependencies {
    classpath "gradle.plugin.io.github.C0deMat:icenterjsgradlecompiler:0.4.0"
  }
}

apply plugin: "io.github.C0deMat.icenterjsgradlecompiler"
```


#### Use the plugin
The usage of the plugin it's pretty simple, first you define the options (inside the *build.gradle*):


```groovy
jsOptions {  
  inputPath = file("./resources/custom/")  
  outputPath = file("./resources/custom/minified/")  
  compilationLevel = "SIMPLE_OPTIMIZATIONS"  
  jsVersionIn = 'ECMASCRIPT_2015'  
  jsVersionOut = 'ECMASCRIPT5'  
  combineAllFiles = false  
  keepSameName = false  
}
```

|Option                  |Type    |Description                                                                                                                                                                                                              |
|------------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|inputPath*              |String  |It tells the plugin where to search input files (not recursive)                                                                                                                                                          |
|outputPath              |String  |Path where output should be saved. Can be a directory or a single file. If it is a directory it will be used the input file name (the same behaviour is used if it is a file but the flag *combineAllFiles* is **false**)|
|compilationLevel        |String  |[Possible values](https://developers.google.com/closure/compiler/docs/compilation_levels): WHITESPACE_ONLY, SIMPLE_OPTIMIZATIONS or ADVANCED_OPTIMIZATIONS                                                               |
|jsVersionIn             |String  |[Possible values](https://javadoc.io/doc/com.google.javascript/closure-compiler/latest/com/google/javascript/jscomp/CompilerOptions.LanguageMode.html)                                                                   |
|jsVersionOut            |String  |[Possible values](https://javadoc.io/doc/com.google.javascript/closure-compiler/latest/com/google/javascript/jscomp/CompilerOptions.LanguageMode.html)                                                                   |
|combineAllFiles         |Boolean |Tells if the output should be merged into single file or the input file name should be preserved                                                                                                                         |
|keepSameName            |Boolean |if true keep the same name of input files otherwise it adds .min (this depends also by the value of combineAllFiles)                                                                                                     |
|recursiveSearchOnSource |Boolean |if true inlcudes js files of sub-folders, excluding the outputPath                                                                                                                                                       |

and then you can call the task:

    compileJs
 
## Built With :hammer:

* [Gradle](https://gradle.org/) - Dependency Management
* [Google Closure Compiler](https://developers.google.com/closure/compiler) - Used to compile js

## Author :boy:

* **Leonardo Bianco** - [leobia](https://leobia.github.io/)

Checkout my Gradle [SassCompiler](https://github.com/leobia/SassGradleCompiler) 

## License :page_facing_up:

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details

