---
title: "String::operator+ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator+"
dev_langs: 
  - "C++"
ms.assetid: 919b5ba4-3d3b-47a4-9893-9a9ce51fb9c8
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator+ 運算子
指出兩個指定的 [String](../cppcx/platform-string-class.md) 物件是否具有相同的值。  
  
## 語法  
  
```cpp  
  
bool String::operator+( String^ str1,  
                         String^ str2)  
  
```  
  
#### 參數  
 `str1`  
 第一個 `String` 物件。  
  
 `str2`  
 第二個 `String` 物件，其內容將會附加至 `str1`。  
  
## 傳回值  
 如果 `true` 等於 `str1`，則為 `str2`，否則為 `false`。  
  
## 備註  
 這個運算子會建立 `String^` 物件，其中包含這兩個運算元的資料。 當極端的效能不重要時，可基於方便的理由使用它。 在函式中呼叫 "`+`" 幾次可能不會被注意到，但是，如果您在緊密迴圈中操作大型物件或文字資料，請使用標準 C\+\+ 機制和類型。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)