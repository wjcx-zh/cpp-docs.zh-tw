---
title: "Object::GetType 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::GetType"
ms.assetid: f633d71a-ff80-49f9-931d-189c00b1f6c5
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::GetType 方法
傳回描述物件之執行階段類型的 [Platform::Type](../cppcx/platform-type-class.md) 物件。  
  
## 語法  
  
```vb  
Object::GetType()  
```  
  
```csharp  
  
```  
  
## 屬性值\/傳回值  
 描述物件之執行階段類型的 [Platform::Type](../cppcx/platform-type-class.md) 物件。  
  
## 備註  
 靜態 [Type::GetTypeCode 方法](../cppcx/type-gettypecode-method.md)可用來取得表示目前類型的 [Platform::TypeCode 列舉](../cppcx/platform-typecode-enumeration.md)值。 這對於內建類型而言非常有用。 除了 [Platform::String](../cppcx/platform-string-class.md) 以外，所有 ref 類別的類型代碼都是 Object \(1\)。  
  
 您可以使用 Windows API 中的 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) 類別在 Windows 元件和應用程式之間傳遞類型資訊，這種方式和使用的語言無關。 T[Platform::Type 類別](../cppcx/platform-type-class.md) 擁有用來在 `Type` 和 `TypeName` 之間轉換的運算子。  
  
 例如，在 XAML 頁面之間瀏覽時，就可以使用 [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) 運算子傳回類別名稱的 `Platform::Type` 物件：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## 請參閱  
 [Platform::Type 類別](../cppcx/platform-type-class.md)   
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)   
 [類型系統](../cppcx/type-system-c-cx.md)