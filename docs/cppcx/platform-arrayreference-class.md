---
title: "Platform::ArrayReference 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ArrayReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ArrayReference 類別"
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ArrayReference 類別
`ArrayReference` 是最佳化類型，當您想要使用輸入資料填入 C\-style 陣列時，可以使用它來替代輸入參數中的 [Platform::Array^](../cppcx/platform-array-class.md)。  
  
## 語法  
  
```vb  
  
```  
  
```csharp  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[ArrayReference::ArrayReference 建構函式](../cppcx/arrayreference-arrayreference-constructor.md)|初始化 `ArrayReference` 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[ArrayReference::operator\(\) 運算子](../cppcx/arrayreference-operator-call-operator.md)|將這個 `ArrayReference` 轉換成 `Platform::Array<T>^*`。|  
|[ArrayReference::operator\= 運算子](../cppcx/arrayreference-operator-assign-operator.md)|將另一個 `ArrayReference` 的內容指派給這個執行個體。|  
  
## 例外狀況  
  
## 備註  
 使用 `ArrayReference` 填滿 C\-style 陣列時，可避免先複製到 `Platform::Array` 變數然後複製到 C\-style 陣列時所牽涉到的額外複製作業。 當您使用 `ArrayReference` 時，只會有一項複製作業。 如需程式碼範例，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 小節標題  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)