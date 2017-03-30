# c
buildscript {
    repositories {
        jcenter()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:2.2.0'
    }
}

apply plugin: 'com.android.application'

repositories {
    jcenter()
}

dependencies {
    compile "com.android.support:support-v4:25.0.1"
    compile "com.android.support:support-v13:25.0.1"
    compile "com.android.support:cardview-v7:25.0.1"
    compile "com.android.support:appcompat-v7:25.0.1"
}

// The sample build uses multiple directories to
// keep boilerplate and common code separate from
// the main sample code.
List<String> dirs = [
    'main',     // main sample code; look here for the interesting stuff.
    'common',   // components that are reused by multiple samples
    'template'] // boilerplate code that is generated by the sample template process

android {
    compileSdkVersion "android-O"
    buildToolsVersion "25.0.2"

    defaultConfig {
        minSdkVersion 21
        targetSdkVersion "android-O"
    }

    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_7
        targetCompatibility JavaVersion.VERSION_1_7
    }

    sourceSets {
        main {
            dirs.each { dir ->
                java.srcDirs "src/${dir}/java"
                res.srcDirs "src/${dir}/res"
            }
        }
        androidTest.setRoot('tests')
        androidTest.java.srcDirs = ['tests/src']

