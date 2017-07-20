# React Native - AlbumApp dengan Expo
# Moh Fiki
## Get Start

Gambaran App yang akan dibuat:

![app-outline](https://lh6.googleusercontent.com/-nc-RsyLjBAY/VGve1G_8h1I/AAAAAAAAAKY/lVT6_ykBrB4/s800/menghapus+repos+github.gif)

* Install [Expo Desktop](https://docs.expo.io/versions/v16.0.0/introduction/installation.html).
* Install Expo App -> Google Play Store or iOS App Store.
* Install [Genymotion].(https://docs.expo.io/versions/v16.0.0/guides/genymotion.html) (Opsional), [Cara Install disni].(https://docs.genymotion.com/Content/01_Get_Started/Installation.htm)
* PadaExpo Desktop: **Create New Project** 
* Atau dengan Commandline sbb: 
    
    exp init namaApp 

* Buka dengan Visual Code Studio dan lakukan update.

* Are work with GIT ??? 
[RN Auth Expo Home Work!](https://github.com/vanbumi/react-native-auth-expo)


## Membuat Header component

Create new folder named src
Create new folder named src/components
Create new file named src/components/Header.js

Tuliskan kode seperti dibawah ini:

    import React from 'react';
    import { Text } from 'react-native';

    const Header = () => {
      return <Text>Album App</Text>
    };

    export default Header;

Update the class App on main.js

    import Header from './src/components/Header';

    class App extends React.Component {
      render() {
        return (
          <Header />
        );
      }
    }

Save and check on device :)

## Add Style

Create JavaScript object for stylist :

    const styles = {
      textStyle: {
        fontSize: 20
      }      
    };

Update Header.js

    const Header = () => {
      const { textStyle } = styles;

      return <Text style={textStyle}>Album App</Text>
    };    

### Add View Tag to wrap Text Tag

![3-wrap-with-view-tag](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_124,w_300/v1499954927/albums-app/3-wrap-with-view-tag.png)

Update Header.js

    const Header = () => {
      const { textStyle, viewStyle } = styles;

      return (
        <View style={viewStyle}>
          <Text>style={textStyle}>Album App</Text>
        </View>
      )
    };

 Update style nya:

    const styles = {
      textStyle: {
        fontSize: 20
      },
      viewStyle: {
        backgroundColor: '#f8f8f8'
      }
    };  
       
## Mengatur Posisi Element dengan Flexbox

**Flexbox** adalah sistim positioning element didalam container.
Mengatur posisi element children oleh parent, parent -> children.
**View Tag -> Text Tag**

### Position Default.

![4-default-position](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_231,w_350/v1499956644/albums-app/4-default-position.png)

### justifyContent.

**justifyContent** digunakan untuk mengatur posisi secara Vertikal.

![5-justify-content](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_218,w_350/v1499957054/albums-app/5-justify-content.png)

![6-justifyConten-center](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_219,w_350/v1499957301/albums-app/6-justifyConten-center.png)

![7-justifyConten-flex-start](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_221,w_350/v1499957471/albums-app/7-justifyConten-flex-start.png)

### alignItems

**alignItems** digunakan untuk mengatur posisi secara Vertikal.

![8-aligIitem-flext-start](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_221,w_350/v1499957661/albums-app/8-aligIitem-flext-start.png)

![9-aligIitem-center](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_224,w_350/v1499957926/albums-app/9-aligIitem-center.png)

![10-aligIitem-flex-end](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_223,w_350/v1499958048/albums-app/10-aligIitem-flex-end.png)

## Header Styling

So Update lagi style nya:

    const styles = {
      textStyle: {
        fontSize: 20
      },
      viewStyle: {
        backgroundColor: '#f8f8f8',
        justifyContent: 'center',
        alignItems: 'center',
        height: 60,
        paddingTop: 15
        ----------------------> test di screen
        shadowColor: '#000',
        shadowOffset: { width: 1, height: 2 },
        shadowOpacity: 0.9,
        elevation: 2,
        position: 'relative'
      }
    };

## Header Reusable

Ini adalah Statik Header Title (hard coded)

    <Text>style={textStyle}>Album App</Text>

Kita ingin header dinamis --> berganti title --> header menjadi reusable.

**Refactor! Parents component to Children component with Props sistem**

Dari main.js <-- root / parent

    <Header headerText={ 'Album Ku' } />

Pada Header.js, menambahkan props object dari parents component:

    <Text style={textStyle}>{props.headerText}</Text>

> catatan* insert javascript variable pada JSX harus diapit dengan **{ }**.

Dan menambahkan reference props, pada function argumentnya:

    const Header = (props) => {

## Cara membuat List Data untuk Album App

Hard coding ? No!

Kita akan mengkonsumsi dari dari sistem online API dengan method HTTP Request.

    https://rallycoding.herokuapp.com/api/music_albums

untuk memudahkan membaca json gunakan plugin **JSON Formatter**.

Component yang akan kita buat adalah

* AlbumList
* AlbumDetail

Dimana AlbumList berisi beberapa AlbumDetail

![11-diagram-albumList](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_537,w_250/v1499961860/albums-app/11-diagram-albumList.png)

AlbumList component yang akan fetching data dari API, kemudian dirender ke masing-masing AlbumDetail component. AlbumDetail hanya bertugas untuk show single Card kepada user. 

## Component Boiler Plate

![12-diagram-fetching-data](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_390,w_700/v1499993800/albums-app/12-diagram-fetching-data.png)

Gambar diatas memberikan gambaran bagaimana Nested Component berjalan, dimana add root, parent & children component berlaku.

Ikuti Step berikut ini:

Membuat component baru AlbumList.js folder src/components/AlbumList.js.

Ada 2 jenis component di dalam React Native

1. class base component:
class base component adalah component Dinamic, digunakan untuk interaktif user dan fetching data. 
2. functional base component:
functional base componet adalah component Statik, di gunakan untuk display data ke user.

Component AlbumList -> class base component -> fetching data -> Ajax request -> provider API.

![13-jenis-component](http://res.cloudinary.com/medioxtra/image/upload/c_scale,h_370,w_700/v1499995776/albums-app/13-jenis-component.png)

Component class base **Boilerplate!**

    import React, { Component } from 'React';
    import { View, Text } from 'react-native';

    class AlbumList extends Component {
      render() {
        return (
           <View>
            <Text>Album List</Text>
           </View> 
        );
      }
    }

    export default AlbumList;

Pada main.js import AlbumList:

Update main.js menjadi sbb:

    import Expo from 'expo';
    import React from 'react';
    import { View } from 'react-native';
    import Header from './src/components/Header';
    import AlbumList from './src/components/AlbumList';

Cara menempatkan AlbumList Tag di dalam main/App.js :

    class App extends React.Component {
      render() {
        return (
          <View}>
            <Header headerText={ 'Album Ku' } />
            <AlbumList />
          </View>
        );
      }
    }

Didalam penulisan JSX berlaku 1 component hanya terdapat 1 single JSX Tag, jadi apabila ada 2 component Tag harus diapit oleh View Tag, lihat contoh diatas.

Pada main.js jangan lupa View Tag di import bila belum:

    import { View } from 'react-native';

Test di pada device !

## Cara fetching data dari API

* Kapan? -> saat App boots up! or load!
* Bagaimana caranya? -> Hook atau event notification -> **lifecycle method**.
* **componentWillMount()**
* Menggunakan library -> Axios.

Update AlbumList.js :

    class AlbumList extends Component {
      componentWillMount() {
        
      }

      render() {
        return (
           <View>
            <Text>Album List</Text>
           </View> 
        );
      }
    }

