
react-speech-recognition
A React hook that converts speech from the microphone to text and makes it available to your React components.

npm version npm downloads license Coverage Status

How it works
useSpeechRecognition is a React hook that gives a component access to a transcript of speech picked up from the user's microphone.

SpeechRecognition manages the global state of the Web Speech API, exposing functions to turn the microphone on and off.

Under the hood, it uses Web Speech API. Note that browser support for this API is currently limited, with Chrome having the best experience - see supported browsers for more information.

This version requires React 16.8 so that React hooks can be used. If you're used to version 2.x of react-speech-recognition or want to use an older version of React, you can see the old README here. If you want to migrate to version 3.x, see the migration guide here.

Useful links
Basic example
Why you should use a polyfill with this library
Cross-browser example
Supported browsers
Polyfills
API docs
Troubleshooting
Version 3 migration guide
TypeScript declaration file in DefinitelyTyped
Installation
To install:

npm install --save react-speech-recognition

To import in your React code:

import SpeechRecognition, { useSpeechRecognition } from 'react-speech-recognition'

Basic example
The most basic example of a component using this hook would be:

import React from 'react';
import SpeechRecognition, { useSpeechRecognition } from 'react-speech-recognition';

const Dictaphone = () => {
  const {
    transcript,
    listening,
    resetTranscript,
    browserSupportsSpeechRecognition
  } = useSpeechRecognition();

  if (!browserSupportsSpeechRecognition) {
    return <span>Browser doesn't support speech recognition.</span>;
  }

  return (
    <div>
      <p>Microphone: {listening ? 'on' : 'off'}</p>
      <button onClick={SpeechRecognition.startListening}>Start</button>
      <button onClick={SpeechRecognition.stopListening}>Stop</button>
      <button onClick={resetTranscript}>Reset</button>
      <p>{transcript}</p>
    </div>
  );
};
export default Dictaphone;








📋 react-use-clipboard
NPM version Test build status Bundle size Bundle size

A React Hook that provides copy to clipboard functionality.

Install
You can install react-use-clipboard with NPM or Yarn.

npm install react-use-clipboard
yarn add react-use-clipboard
Usage
Here's how to use react-use-clipboard:

import useClipboard from "react-use-clipboard";

function App() {
  const [isCopied, setCopied] = useClipboard("Text to copy");

  return (
    <button onClick={setCopied}>
      Was it copied? {isCopied ? "Yes! 👍" : "Nope! 👎"}
    </button>
  );
}
You can reset the isCopied value after a certain amount of time with the successDuration option.

import useClipboard from "react-use-clipboard";

function App() {
  const [isCopied, setCopied] = useClipboard("Text to copy", {
    // `isCopied` will go back to `false` after 1000ms.
    successDuration: 1000,
  });

  return (
    <button onClick={setCopied}>
      Was it copied? {isCopied ? "Yes! 👍" : "Nope! 👎"}
    </button>
  );
}
