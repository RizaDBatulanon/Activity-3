import React, { useState } from 'react';
import { View, Button, Text, Image } from 'react-native';

const MyComponent = () => {
  const [showFlashlight, setShowFlashlight] = useState(false);
  const [showCounter, setShowCounter] = useState(false);
  const [isButtonDisabled, setIsButtonDisabled] = useState(false);
  const [showImageOne, setShowImageOne] = useState(true);
  const [isSwitchToggled, setIsSwitchToggled] = useState(false);
  const [counterValue, setCounterValue] = useState(0);

  const toggleFlashlight = () => {
    setShowFlashlight(!showFlashlight);
    setIsButtonDisabled(true);
  };

  const toggleCounter = () => {
    setShowCounter(!showCounter);
    setIsButtonDisabled(true);
  };

  const toggleImage = () => {
    setShowImageOne(!showImageOne);
    setIsSwitchToggled(!isSwitchToggled);
  };

  const incrementCounter = () => {
    setCounterValue(counterValue + 1);
  };

  const decrementCounter = () => {
    if (counterValue > 0) {
      setCounterValue(counterValue - 1);
    }
  };

  const toggleComponentVisibility = () => {
    setShowFlashlight(null);
    setShowCounter(null);
    setIsButtonDisabled(false);
  };

  return (
    <View style={{ flex: 1, alignItems: 'center', height: '100%' }}>
      <View
        style={{
          flexDirection: 'row',
          marginTop: 40,
          marginBottom: 80,
          justifyContent: 'space-evenly',
          width: 200,
        }}
      >
        <Button
          title="Flashlight"
          onPress={toggleFlashlight}
          disabled={isButtonDisabled}
          style={{ width: 200 }}
        />
        <Button
          title="Counter"
          onPress={toggleCounter}
          disabled={isButtonDisabled}
          style={{ width: 200 }}
        />
      </View>
      <View style={{ width: 200, justifyContent: 'center', alignItems: 'center' }}>
        {showFlashlight && (
          <View style={{ width: 200 }}>
            <View style={{ marginBottom: 80 }}>
              {showImageOne ? (
                <Image
                  source={{
                    uri:
                      'https://th.bing.com/th/id/R.f9dff3bbdfa82068a3283a81a319c1ce?rik=go%2f9k0N48nYu6g&riu=http%3a%2f%2fpngimg.com%2fuploads%2fflashlight%2fflashlight_PNG55995.png&ehk=3yTEkx7IMniAqE%2fRtb8TbQCO%2bq36%2fwpaBwc%2fvSAVGjM%3d&risl=&pid=ImgRaw&r=0',
                  }} // DEFAULT
                  style={{ width: 500, height: 300, marginBottom: 30 }}
                />
              ) : (
                <Image
                  source={{
                    uri:
                      'https://www.freepngimg.com/thumb/flashlight/22814-1-flashlight.png',
                  }} // SWITCH
                  style={{ width: 750, height: 300, marginBottom: 30 }}
                />
              )}
              {isSwitchToggled ? (
                <Button title="Off" color={'black'} onPress={toggleImage} style={{ width: 200 }} />
              ) : (
                <Button title="On" color={'#000000'} onPress={toggleImage} style={{ width: 200 }} />
              )}
            </View>
            <Button
              title={showFlashlight ? 'Back' : 'Show Component'}
              onPress={toggleComponentVisibility}
            />
          </View>
        )}

        {showCounter && (
          <View style={{ width: 300 }}>
            <View style={{ justifyContent: 'center', alignItems: 'center' }}>
              <Text style={{ fontSize: 200, fontWeight: 'bold' }}>{counterValue}</Text>
            </View>
            {
              <View style={{ flexDirection: 'row', justifyContent: 'space-evenly', marginTop: 60 }}>
                <Button title="+1 Increment" color={'#000000'} onPress={incrementCounter} style={{ width: 100 }} />
                <Button title="-1 Decrement" color={'#000000'} onPress={decrementCounter} style={{ width: 100 }} />
              </View>
            }
            <View style={{ width: 200, marginTop: 50 }}>
              <Button title={showCounter ? 'Back' : ''} onPress={toggleComponentVisibility} />
            </View>
          </View>
        )}
      </View>
    </View>
  );
};

export default MyComponent;
