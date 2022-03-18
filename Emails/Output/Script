#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Wed Feb 20 16:14:16 2022

@author: JJ EC
"""


import csv
import os
import copy

cwd = os.getcwd()
file_list = os.listdir(cwd)
file=[]

Dates = {}
CO2_Dates = {}
HCHO_Dates = {}
PM10_Dates = {}
PM25_Dates = {}
TVOC_Dates = {}

Locations = {}#'B61':,'B62':,'B71':,'B7-AVG':,'B81':,'B82':,'B83':,'B8-AVG':,'C1':,'C2':,'C - AVG':,'G1':,'G2':,'G3':,'G-AVG':,'SH1':,'SY1':,'SY2':,'SY3':,'SY4':,'SY-AVG':,'K1':,'K2':,'K3':,'K-AVG':,'N3F1':,'N3F2':,'N3-AVG':,'N4F1':,'N4F2':,'N4-AVG':'XIN':}
Locations['Date'] = 'Date' 
Locations['7210004994FC'] = 'B6F1' #B73 #now B6F1
Locations['7210003B41A2'] = 'B6F2' #B83 72100034AE53 #now B6F2 '7210003B41A2'
Locations['B6-avg'] = None
Locations['72100034AE53'] = 'B7F1' #B7F1 72100027FC71
Locations['72100027FC71'] = 'B7F1old' #B7F1old 72100027FC71
Locations['7210002FF4F0'] = 'B7F2' #B7F2 
Locations['B7-avg'] = None
Locations['7210003A60B2'] = 'B10F1' #B10F1
Locations['7210002B70B0'] = 'B10F2' #B10F2 
Locations['B10-avg'] = None
Locations['7210005D21AE'] = 'C1' #C1
Locations['7210003FC5E2'] = 'C2' #C2
Locations['C-avg'] = None
Locations['7210002ED5E0'] = 'G1' #G1
Locations['721000358F43'] = 'G2' #G2
Locations['7210002DB6D0'] = 'G3' #G3
Locations['G-avg'] = None
Locations['72100040BD6D'] = 'SH1' #SH1
Locations['72100045183D'] = 'SH2' #SH2

Locations['72100052CE5F'] = 'SPS' #SPS

Locations['721000281380'] = 'SPX1' #SPX1
Locations['721000382292'] = 'SPX2' #SPX2

Locations['72100048B5EC'] = 'SY1' #SY1
Locations['72100042FF4D'] = 'SY2' #SY2
Locations['7210005BE7CE'] = 'SY3' #SY3
Locations['72100043DE5D'] = 'SY4' #SY4
Locations['SY-avg'] = None
Locations['72100053EF4F'] = 'K1' #K1
Locations['72100061FE59'] = 'K2' #K2
Locations['721000657A19'] = 'K3' #K3
Locations['K-avg'] = None
Locations['721000564A1F'] = 'N3F1' #N3F1
Locations['7210005F638E'] = 'N3F2' #N3F2
Locations['N3F-avg'] = None
Locations['72100063BC79'] = 'N4F1' #N4F1
Locations['721000645B09'] = 'N4F2' #N4F2
Locations['N4F-avg'] = None
Locations['721000629D69'] = 'Xin' #XIN
Locations['72100055292F'] = 'OV' #OV1


HCHO = dict.fromkeys(Locations)
HCHO['Date'] =  None
PM10 = dict.fromkeys(Locations)
PM10['Date'] = None 
PM25 = dict.fromkeys(Locations)
PM25['Date'] = None 
TVOC = dict.fromkeys(Locations)
TVOC['Date'] = None
CO2 = dict.fromkeys(Locations)
CO2['Date'] = None 

Particles = [PM25, PM10, HCHO, TVOC, CO2]


for files in file_list:
    if files.endswith(".csv") and len(files)> 14:
        file.append(files)
        
        
for i in file:
    with open(i, 'r') as csv_file:
        reader = csv.reader(csv_file)
        
        count = 0
        Data = 0
        
        for row in reader:
    
            count = count + 1
            if count == 1:
                ID = row[1].strip()
            elif count == 2:
                Sensor = row[0]
            elif count < 193:
                continue
            else:
                if row[0].isdigit() or row[0][2:].isdigit():
                    Data = Data + float(row[0])
                else:
                    continue
            
        Date = row[1].split()[0].replace('/','-')
        Average = Data/97
        
        
        if Sensor == 'HCHO':
            if int(Date[-2:]) in HCHO_Dates:
                print("adding")
            else:
                print("creating")
                HCHO_Dates[int(Date[-2:])] = dict.fromkeys(HCHO)
                
            HCHO_Dates[int(Date[-2:])][ID] = Average
            HCHO_Dates[int(Date[-2:])]['Date'] = Date
            
        
        elif Sensor == 'PM2.5':
            if int(Date[-2:]) in PM25_Dates:
                print("adding",ID)
            else:
                print("creating",ID)
                PM25_Dates[int(Date[-2:])] = dict.fromkeys(PM25)
                
            PM25_Dates[int(Date[-2:])][ID] = Average
            PM25_Dates[int(Date[-2:])]['Date'] = Date
            
        elif Sensor == 'PM10':
            if int(Date[-2:]) in PM10_Dates:
                print("adding")
            else:
                print("creating")
                PM10_Dates[int(Date[-2:])] = dict.fromkeys(PM10)
                
            PM10_Dates[int(Date[-2:])][ID] = Average
            PM10_Dates[int(Date[-2:])]['Date'] = Date
            
            
            
        elif Sensor == 'TVOC':
            if int(Date[-2:]) in TVOC_Dates:
                print("adding")
            else:
                print("creating")
                TVOC_Dates[int(Date[-2:])] = dict.fromkeys(TVOC)
                
            TVOC_Dates[int(Date[-2:])][ID] = Average
            TVOC_Dates[int(Date[-2:])]['Date'] = Date
            
        elif Sensor == 'CO2':
            if int(Date[-2:]) in CO2_Dates:
                print("adding")
            else:
                print("creating")
                CO2_Dates[int(Date[-2:])] = dict.fromkeys(CO2)
                
            CO2_Dates[int(Date[-2:])][ID] = Average
            CO2_Dates[int(Date[-2:])]['Date'] = Date
    
        else:
            print('error')
        
        
        #print(Date, ID, Sensor+':',Average)
        
        csv_file.close()
        
print(PM25_Dates.keys())
print(PM10_Dates.keys())
print(HCHO_Dates.keys())
print(CO2_Dates.keys())
print(TVOC_Dates.keys())

    
with open('PM10'+'.csv', 'w', newline='') as csvfile:
    
    fieldnames = []
    for key in Locations.keys():
        fieldnames.append(key)
    
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    writer.writeheader()
    
    for i in sorted(PM10_Dates.keys()):
            writer.writerow(PM10_Dates[i])
    
    csvfile.close()
    
with open('PM25'+'.csv', 'w', newline='') as csvfile:
    
    fieldnames = []
    for key in Locations.keys():
        fieldnames.append(key)
    
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    writer.writeheader()
    
    for i in sorted(PM25_Dates.keys()):
            writer.writerow(PM25_Dates[i])
    
    csvfile.close()
    
with open('HCHO'+'.csv', 'w', newline='') as csvfile:
    
    fieldnames = []
    for key in Locations.keys():
        fieldnames.append(key)
    
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    writer.writeheader()
    
    for i in sorted(HCHO_Dates.keys()):
            writer.writerow(HCHO_Dates[i])
    
    csvfile.close()
    
with open('CO2'+'.csv', 'w', newline='') as csvfile:
    
    fieldnames = []
    for key in Locations.keys():
        fieldnames.append(key)
    
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    writer.writeheader()
    
    for i in sorted(CO2_Dates.keys()):
            writer.writerow(CO2_Dates[i])
    
    csvfile.close()
    
with open('TVOC'+'.csv', 'w', newline='') as csvfile:
    
    fieldnames = []
    for key in Locations.keys():
        fieldnames.append(key)
    
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    writer.writeheader()
    
    for i in sorted(TVOC_Dates.keys()):
            writer.writerow(TVOC_Dates[i])
    
    csvfile.close()
