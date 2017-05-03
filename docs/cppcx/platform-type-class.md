---
title: "Platform::Type 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Type 類別"
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Type 類別
包含與類型 \(特別是此項\)、字串名稱和 typecode 相關的執行階段資訊。 可以透過針對任何物件呼叫 [Object::GetType 方法](../cppcx/object-gettype-method.md)或針對類別或結構名稱使用 [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) 運算子取得。  
  
## 語法  
  
```cpp  
public ref class Platform::Type :      Platform::Object,      Platform::Details::IEquatable,      Platform::Details::IPrintable  
```  
  
## 備註  
 在必須使用 `Type` 或 `if` 陳述式 \(可根據物件的執行階段類型加以分支處理\) 進行直接處理的應用程式中，`switch` 類別非常有用。 使用 [Type::GetTypeCode 方法](../cppcx/type-gettypecode-method.md)成員函式可以取得描述類型分類的類型代碼。  
  
## 公用方法  
  
|||  
|-|-|  
|[Type::GetTypeCode 方法](../cppcx/type-gettypecode-method.md)|傳回物件的 [Platform::TypeCode 列舉](../cppcx/platform-typecode-enumeration.md)值。|  
  
## 公用屬性  
  
|||  
|-|-|  
|[Type::FullName 屬性](../cppcx/type-fullname-property.md)|傳回表示類型之完整名稱的 [Platform::String 類別](../cppcx/platform-string-class.md)^，並使用 .  \(點\) 而非 :: \(雙冒號\) 做為分隔符號，例如 "MyNamespace.MyClass"。|  
  
## 轉換運算子  
  
|||  
|-|-|  
|[運算子 Type^](../cppcx/operator-subtracttype-hat.md)|可以從 `Windows::UI::Xaml::Interop::TypeName` 轉換為 `Platform::Type`。|  
|[運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)|可以從 `Platform::Type` 轉換為 `Windows::UI::Xaml::Interop::TypeName`。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)