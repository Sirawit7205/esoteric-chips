# Esoteric Chips

## Introduction

This repo contains an index for hard to find IC chips. 

Many websites that sell these chips often don't have great parameterized search functions like major distributors. This is unfortunate because sometimes nice and cheap chips are buried deep within a list of thousands others, hidden from view. I really hope that this "index" with be able to help.

## How to Use

Right now the information is available in JSON files. There is a plan to build a web application for this repo later but there is no guaranteed.

Information are separate into two directories:

 - **parts:** Listing of actual devices, with categories 
 - **mfgs:** Listing of device manufacturers and package types they use.

## Disclaimer

 - Although I tried to check that every information in this repo is accurate, some mistakes might be present. It is your responsibility to cross-check the information with the official device datasheets before making decisions. I do not accept any responsibilities over any damage from using this repo.
 - Device Information in this repo belongs to its respective manufacturers. I do not claim any information as mine.

## Contribution Guidelines

### General

 - Put new information in `dev` branch.
 - Make sure you follow the data format provided below.
 - Add/Edit parts manufacturer before adding parts itself.

### Parts

Part files are stored in JSON format, with the information as follows.

 - **name** This is the main part number.
	 - Remove any other info such as speed grade, package, temperature grade, or carrier information out.
 - **mfg** Manufacturer name.
	 - Same as `name` field in manufacturer's JSON file. 
 - **cat** Main category of the part.
	 - Check directory structure for information.
 - **subcat** Subcategory.
	 - Check directory structure for information.
 - **description** Some description about the part.
 - **datasheet** URL link to part's datasheet file.
	 - Direct link to manufacturer's site is preferred.
	 - If not possible, link to distributor's site.
 - **variantcode** Formatting for forming orderable part numbers.
	 - [name] for main device name
	 - [package] for package code
	 - others will soon follow
 - **packages** Object containing information about each package type available for this device.
	 - Key for each object is a code designate each package/variant. Then for each key insert an object as follow:
	 - **package** Name of the package as listed in the datasheet.
	 - **pincount** Amount of pins/pads on the device, including thermal pads. Datatype number.
	 - **subdesc** Some additional description of this variant.
	 - **pinout** Object containing pinout information of this variant.
		 - Example > "1" : "VCC"
		 - Example > "8" : "RX"
		 - Use exact pinout name as listed in the datasheet.
		 - If the device has a thermal pad, always assign the highest pin number for it.

### Manufacturers

Manufacturer files are stored in JSON format, with the information as follows.

 - **name** Short manufacturer name, for use with part files.
 - **fullname** Full manufacturer name.
 - **website** Manufacturer's website.
 - **packagelinks** JSON object containing information about the chip packages this manufacturer uses.
	 - Key of each object is the package name the manufacturer uses.
	 - Data of each object is the matching package footprint name in Kicad.
	 - If the footprint is not available in Kicad, put "N/A".



