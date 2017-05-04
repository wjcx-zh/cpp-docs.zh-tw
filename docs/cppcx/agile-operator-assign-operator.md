---
title: "Agile::operator= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::operator="
ms.assetid: 2c413bef-f103-4911-afb3-0dac5f6a760e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::operator= 運算子
將指定的物件指派給目前 Agile 物件。  
  
## 語法  
  
```cpp  
  
   Agile<T> operator=(  
   T^ object  
) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### 參數  
 `T`  
 typename 樣板指定的類型。  
  
 `object`  
 複製或移至目前 Agile 物件的物件或物件控制代碼。  
  
 `lp`  
 物件的 IUnknown 介面指標。  
  
## 傳回值  
 `T` 類型物件的控制代碼  
  
## 備註  
 指派運算子的第一個版本會將參考類型的控制代碼複製到目前 Agile 物件。 第二個版本複製 Agile 類型的參考至目前 Agile 物件。 第三個版本移動 Agile 類型至目前 Agile 物件。 第四個版本移動 COM 物件的指標至目前 Agile 物件。  
  
 指派作業會自動保存目前 Agile 物件的內容。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Agile 類別](../cppcx/platform-agile-class.md)