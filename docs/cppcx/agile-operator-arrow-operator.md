---
title: "Agile::operator-&gt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::operator->"
ms.assetid: 570f4b0b-1735-49b3-8a30-4a302ac57074
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::operator-&gt; 運算子
擷取目前 Agile 物件所代表的物件控制代碼。  
  
## 語法  
  
```cpp  
  
       T^ operator->()   
const throw();  
```  
  
## 傳回值  
 目前 Agile 物件所代表的物件控制代碼。  
  
 這個運算子實際傳回保密的內部類型。 若要保留傳回值，將它指派給使用 [auto](~/cpp/auto-cpp.md) 類型推斷關鍵字宣告的變數，會是很方便的方式。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Agile 類別](../cppcx/platform-agile-class.md)