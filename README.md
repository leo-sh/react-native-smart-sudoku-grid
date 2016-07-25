# react-native-smart-sudoku-grid

A smart sudoku grid layout for react-native apps. Written in JS for cross-platform support.
It works on iOS and Android.

This component is compatible with React Native 0.25 and newer.

## Preview

![react-native-smart-sudoku-grid-preview][1]
![react-native-smart-sudoku-grid-preview-android][3]

## Installation

```
npm install react-native-smart-sudoku-grid --save
```

## Usage

Install the SudokuGrid from npm with `npm install react-native-smart-sudoku-grid --save`.
Then, require it from your app's JavaScript files with `import SudokuGrid from 'react-native-smart-sudoku-grid'`.

```js
import React, {
  Component,
} from 'react'
import {
  ScrollView,
  StyleSheet,
  View,
  Image,
  Text,
  TouchableHighlight,
  Alert,
} from 'react-native'

import SudokuGrid from 'react-native-smart-sudoku-grid'
import CornerLabel from 'react-native-smart-corner-label'

import image_cash from '../images/cash.png'
import image_credit from '../images/credit.png'
import image_transfer from '../images/transfer.png'
import image_loan from '../images/loan.png'
import image_charge from '../images/charge.png'
import image_payment from '../images/payment.png'
import image_shopping from '../images/shopping.png'
import image_service from '../images/service.png'
import image_donate from '../images/donate.png'

const dataList = [
  {
    icon: image_cash,
    title: 'cash',
  },
  {
    icon: image_credit,
    title: 'credit',
  },
  {
    icon: image_transfer,
    title: 'transfer',
  },
  {
    icon: image_loan,
    title: 'loan',
  },
  {
    icon: image_charge,
    title: 'charge',
  },
  {
    icon: image_payment,
    title: 'payment',
  },
  {
    icon: image_shopping,
    title: 'shopping',
  },
  {
    icon: image_service,
    title: 'service',
  },
  {
    icon: image_donate,
    title: 'donate',
  },
]

const columnCount = 3

export default class ThreeColumns extends Component {

  render() {
      return (
          <ScrollView style={{marginTop: 44 + 20, backgroundColor: '#fff', }}>
            <View style={{height: 30, paddingLeft: 10, backgroundColor: '#E1E5E8', justifyContent: 'center', }}>
              <Text>Services: </Text>
            </View>
            <SudokuGrid
              containerStyle={{ backgroundColor: '#fff',}}
              columnCount={columnCount}
              dataSource={dataList}
              renderCell={this._renderGridCell}
            />
          </ScrollView>
      )
  }

  _renderGridCell = (data, index, list) => {
      return (
          <TouchableHighlight underlayColor={'#eee'} onPress={ this._onPressCell.bind(this, data, index) }>
            <View style={{ overflow: 'hidden',
                          justifyContent: 'center', alignItems: 'center', height: 100,
                          borderBottomWidth: StyleSheet.hairlineWidth, borderColor: '#eee',
                          borderRightWidth: (index + 1) % columnCount ? StyleSheet.hairlineWidth: 0, }}>
              <Image source={data.icon} style={{width: 30, height: 30, marginHorizontal: 10, marginBottom: 10,}}/>
              <Text>{data.title}</Text>
              { index == 6 ?
                <CornerLabel
                  cornerRadius={54}
                  style={{backgroundColor: 'red', height: 24,}}
                  textStyle={{color: '#fff', }}>
                  30% off
                </CornerLabel> : null
              }
            </View>
          </TouchableHighlight>
      )
  }

  _onPressCell(data, index) {
      Alert.alert('clicked ' + data.title)
  }

}
```

## Props

Prop            | Type   | Optional | Default     | Description
--------------- | ------ | -------- | ----------- | -----------
rowWidth        | number | Yes      | deviceWidth | determines the width of a row.
columnCount     | number | No       |             | determines how many columns a row contains.
dataSource      | array  | No       |             | determines the datasource of grid
renderCell      | func   | No       |             | A function that returns the grid cell component.
style           | style  | Yes      |             | see [react-native documents][2]


[1]: http://cyqresig.github.io/img/react-native-smart-sudoku-grid-preview-ios-v1.0.7.gif
[2]: https://facebook.github.io/react-native/docs/style.html
[3]: http://cyqresig.github.io/img/react-native-smart-sudoku-grid-preview-android-v1.0.7.gif
