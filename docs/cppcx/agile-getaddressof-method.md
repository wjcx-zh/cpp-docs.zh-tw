---
title: "Agile::GetAddressOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::GetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::GetAddressOf"
ms.assetid: f015edf9-4155-4992-a6fc-7ff1edcc5d1e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::GetAddressOf 方法
重新初始化目前 Agile 物件，然後傳回 `T` 類型物件的控制代碼位址。  
  
## 語法  
  
```cpp  
  
       T^* GetAddressOf()   
throw();  
```  
  
#### 參數  
 `T`  
 樣板 typename 參數指定的類型。  
  
## 傳回值  
 `T` 類型物件的控制代碼位址。  
  
## 備註  
 這個作業釋放 `T` 類型物件的目前表示 \(如果有的話\)、重新初始化 Agile 物件的資料成員、取得目前執行緒內容，然後傳回可以代表非 Agile 物件的物件控制代碼變數位址。 若要讓 Agile 類別執行個體代表物件，請使用指派運算子 \([Agile::operator\=](../cppcx/agile-operator-assign-operator.md)\)，將物件指派給 Agile 類別執行個體。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Agile 類別](../cppcx/platform-agile-class.md)