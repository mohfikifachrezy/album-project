# React Native - AlbumApp dengan Expo
# Moh Fiki
## Get Start

Gambaran App yang akan dibuat:

![app-outline](https://lh6.googleusercontent.com/-nc-RsyLjBAY/VGve1G_8h1I/AAAAAAAAAKY/lVT6_ykBrB4/s800/menghapus+repos+github.gif)

<object width="425" height="350">
  <param name="movie" value="http://www.youtube.com/user/wwwLoveWatercom?v=BTRN1YETpyg" />
  <param name="wmode" />
  <embed src="http://www.youtube.com/user/wwwLoveWatercom?v=BTRN1YETpyg"
         type="application/x-shockwave-flash"
         width="425" height="350" />
</object>

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

![3-wrap-with-view-tag](http://haloponsel.com/wp-content/uploads/2016/11/dp-bbm-bergerak-keren-oppan-gangnam-style.gif)

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
       
