#project baru ni

##lumayan berat

Selamat Datang Di Pembelajaran React Native

import React, { Component } from 'react';
import { Text, View, StyleSheet, Image, Button, Alert } from 'react-native';
import { Constants } from 'expo';

export default class App extends Component {
  _handleButtonPress = () => {
    Alert.alert(
      'Makasih Telah Melihat',
      'coba lagi',
    );
  };

  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.paragraph}>
          Change code in the editor and watch it change on your phone!
          Save to get a shareable url. You get a new url each time you save.
        </Text>
        <Image
          source={{ uri: 'http://d23dyxeqlo5psv.cloudfront.net/cat.gif' }}
          style={{ height: 140, width: 200 }}
        />
        <Button
          title="Press me"
          onPress={this._handleButtonPress}
        />
      
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
    paddingTop: Constants.statusBarHeight,
    backgroundColor: '#ecf0f1',
  },
  paragraph: {
    margin: 24,
    fontSize: 18,
    fontWeight: 'bold',
    textAlign: 'center',
    color: '#34495e',
  },
});
