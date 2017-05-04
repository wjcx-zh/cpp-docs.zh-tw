---
title: "Platform::Array 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Array 類別"
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Array 類別
表示可修改的一維陣列，可在不同的應用程式二進位介面 \(ABI\) 之間接收和傳遞。  
  
## 語法  
  
```cpp  
  
template <typename T>  
    private ref class Array<TArg,1> :   
         public WriteOnlyArray<TArg, 1>,  
         public IBoxArray<TArg>  
  
```  
  
## 成員  
 Platform::Array 會從 [Platform::WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)繼承其所有方法，並且實作 `Value`的 [Platform::IBoxArray 介面](../cppcx/platform-iboxarray-interface.md) 屬性。  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[陣列建構函式](../cppcx/array-constructors.md)|初始化由類別範本參數 *T* 所指定之可修改的一維類型陣列。|  
  
### 方法  
 請參閱 [Platform::WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)。  
  
### 屬性  
  
|||  
|-|-|  
|[Array::Value 屬性](../cppcx/array-value-property.md)|擷取目前陣列的控制代碼。|  
  
## 備註  
 Array 類別已密封，無法被繼承。  
  
 Windows 執行階段類型系統不支援不規則陣列的概念，因此您也就不能傳遞 IVector\<Platform::Array\<T\>\> 做為傳回值或方法參數。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。  
  
 如需 Platform::Array 的使用時機與方式的詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
 Windows 執行階段類型系統不支援不規則陣列的概念，因此您也就不能傳遞 IVector\<Platform::Array\<T\>\> 做為傳回值或方法參數。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。  
  
 此類別定義於編譯器會自動納入的 vccorlib.h 標頭中。 它可在 Intellisense 中看到，但是在物件瀏覽器中看不到，因為它不是 platform.winmd 中所定義的公用類型。  
  
## 需求  
 編譯器選項：**\/ZW**  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)