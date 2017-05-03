---
title: "Platform::WriteOnlyArray 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
s.suite: 
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::WriteOnlyArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::WriteOnlyArray 類別"
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
caps.latest.revision: 11
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 11
---
# Platform::WriteOnlyArray 類別
表示一維陣列。當呼叫端傳遞陣列讓方法填滿其中元素時，就會將這個陣列當做輸入參數來傳遞。  
  
 這個 ref 類別在 vccorlib.h 中是宣告為私用，因此不會在中繼資料內發出，而且只能從 C\+\+ 使用。 這個類別只做為用來接收呼叫端所配置之陣列的輸入參數。 您無法從使用者程式碼建構這個類別。 它可以讓 C\+\+ 方法直接在陣列中寫入資料，這就稱為「*FillArray*」模式。 如需詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## 語法  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
## 成員  
  
### 公用方法  
 這些方法的存取範圍都是 internal，也就是說，您只能在 C\+\+ 應用程式或元件內存取這些方法。  
  
|名稱|描述|  
|--------|--------|  
|[WriteOnlyArray::begin 方法](../cppcx/writeonlyarray-begin-method.md)|指向陣列中第一個元素的迭代器。|  
|[WriteOnlyArray::Data 屬性](../cppcx/writeonlyarray-data-property.md)|資料緩衝區的指標。|  
|[WriteOnlyArray::end 方法](../cppcx/writeonlyarray-end-method.md)|指向陣列中最後一個元素後加一的迭代器。|  
|[WriteOnlyArray::FastPass 屬性](../cppcx/writeonlyarray-fastpass-property.md)|表示陣列是否可以使用 FastPass 機制，這是由系統悄悄執行的最佳化作業。 請勿在您的程式碼中使用此屬性。|  
|[WriteOnlyArray::Length 屬性](../cppcx/writeonlyarray-length-property.md)|傳回陣列中的元素數目。|  
|[WriteOnlyArray::set 函式](../cppcx/writeonlyarray-set-function.md)|為指定的元素設定指定的值。|  
  
## 繼承階層  
 `WriteOnlyArray`  
  
## 需求  
 編譯器選項：**\/ZW**  
  
 **中繼資料：**Platform.winmd  
  
 **命名空間：**Platform  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [在 C\+\+ 中建立 Windows 執行階段元件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)