---
title: "ComPtr::operator&amp; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::operator&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator& 運算子"
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator&amp; 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

釋放與這個物件 `ComPtr` 相關的介面然後擷取 `ComPtr` 物件的位址。  
  
## 語法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## 傳回值  
 對目前 `ComPtr`的弱式參考。  
  
## 備註  
 這個方法與 [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) 不同，這個方法會釋放此介面指標的參考。  使用 `ComPtr::GetAddressOf` ，當您需要介面指標的位址但不想發行該介面時。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)