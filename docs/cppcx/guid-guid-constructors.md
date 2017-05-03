---
title: "Guid::Guid 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid::Guid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Guid::Guid"
  - "Guid::Guid"
ms.assetid: dfa4dcad-1c3b-481f-9f60-05141b9788d1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Guid::Guid 建構函式
初始化 Guid 結構的新執行個體。  
  
## 語法  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  
);  
  
    Guid(   
        GUID m  
);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n  
);  
```  
  
#### 參數  
 `a`  
 GUID 的前 4 個位元組。  
  
 `b`  
 GUID 接下來的 2 個位元組。  
  
 `c`  
 GUID 接下來的 2 個位元組。  
  
 `d`  
 GUID 的下一個位元組。  
  
 `e`  
 GUID 的下一個位元組。  
  
 `f`  
 GUID 的下一個位元組。  
  
 `g`  
 GUID 的下一個位元組。  
  
 `h`  
 GUID 的下一個位元組。  
  
 `i`  
 GUID 的下一個位元組。  
  
 `j`  
 GUID 的下一個位元組。  
  
 `k`  
 GUID 的下一個位元組。  
  
 `m`  
 所定義的 GUID。  
  
 `n`  
 GUID 剩餘的 8 個位元組。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::Guid 實值類別](../cppcx/platform-guid-value-class.md)