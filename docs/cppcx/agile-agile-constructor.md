---
title: "Agile::Agile 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::Agile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::Agile"
ms.assetid: 33c1df82-f5db-4750-98cc-0daa03be4e59
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::Agile 建構函式
初始化 Agile 類別的新執行個體。  
  
## 語法  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### 參數  
 `T`  
 樣板 typename 參數指定的類型。  
  
 `object`  
 在此建構函式的第二個版本中，是用來初始化新 Agile 執行個體的物件。 在第三個版本中，是複製到新 Agile 執行個體的物件。 在第四個版本中，是移動到新 Agile 執行個體的物件。  
  
## 備註  
 此建構函式的第一個版本是預設建構函式。 第二個版本從 `object` 參數指定之物件，初始化新的 Agile 執行個體類別。 第三個版本是複製建構函式。 第四個版本是移動建構函式。 這個建構函式不會擲回例外狀況。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Agile 類別](../cppcx/platform-agile-class.md)