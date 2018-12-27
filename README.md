# ARKit-SCNPath

Functions and classes for creating path geometries in a SceneKit application on iOS. Main use-case being for ARKit.

[![Version](https://img.shields.io/cocoapods/v/SCNPath.svg)](https://cocoapods.org/pods/SCNPath)
[![License](https://img.shields.io/cocoapods/l/SCNPath.svg)](https://cocoapods.org/pods/SCNPath)
[![Platform](https://img.shields.io/cocoapods/p/SCNPath.svg)](https://cocoapods.org/pods/SCNPath)
[![Swift 4.2](https://img.shields.io/badge/Swift-4.2-orange.svg?style=flat)](https://swift.org/)
[![CI Status](http://img.shields.io/travis/maxxfrazer/ARKit-SCNPath.svg?style=flat)](https://travis-ci.org/maxxfrazer/ARKit-SCNPath)

## Introduction

Navigation seems to be a strong point for people making AR apps. So here's a class to easily create a path in AR along a set of centre points. This class can also be used to draw out a racetrack, road for an animated character to follow, or even draw a pentagram on the floor!

I'll be releasing a full tutorial shortly after Xmas on my [Medum page](https://medium.com/@maxxfrazer) on how I made the examples in the below gifs using this Pod and about 30 lines of non boilerplate code.

Please feel free to use and contribute this library however you like.
I only ask that you let me know when you're doing so, so I can see some cool uses of it!

## Example

It's as easy as this to make a node with this path as a geometry:

```
let pathNode = SCNPathNode(path: [
	SCNVector3(0,-1,0),
	SCNVector3(0,-1,-1),
	SCNVector3(1,-1,-1)
])
```

Alternatively, you can grab the geometry directly:

```
let pathGeometry = SCNGeometry.path(path: [
	SCNVector3(0,-1,0),
	SCNVector3(0,-1,-1),
	SCNVector3(1,-1,-1)
])
```

The y value is set to -1 just as an example that assumes the origin of your scene graph is 1m above the ground. Use plane detection to actually hit the ground correctly.

Other parameters that can be passed into both the SCNPathNode class and the SCNGeometry.path functions:

| name          | description                                                                     | default            | example                         |
|---------------|---------------------------------------------------------------------------------|--------------------|---------------------------------|
| path          | Array of SCNVector3 points to make up the path                                  | no default         | [SCNVector3(0,-1,0),  SCNVector3(0,-1,-1),  SCNVector3(1,-1,-1)] |
| width         | width of the path in meters                                                     | 0.5                | 0.1                             |
| curvePoints   | number of points to make up the curved look when the path is turning to a new direction.    | 8                  | 16                              |
| materials     | materials to be applied to the geometry.                                                    | a blue SCNMaterial | [SCNMaterial()]                 |
| curveDistance | distance from the centre of the curve as a multiple of half the width to set the corner radius. Minimum value is 1. | 1.5                | 2       |


Here's some basic examples of what you can do with this Pod:

![Path Example 1](https://github.com/maxxfrazer/ARKit-SCNPathNode/blob/master/media/path-example-1.gif)
![Path Example Texture Repeating](https://github.com/maxxfrazer/ARKit-SCNPathNode/blob/master/media/path-example-2.gif)
![Path Example Creating](https://github.com/maxxfrazer/ARKit-SCNPathNode/blob/master/media/path-example-3.gif)
