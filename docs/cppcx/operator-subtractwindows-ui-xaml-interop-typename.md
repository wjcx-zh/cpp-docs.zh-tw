---
title: "運算子 Windows::UI::Xaml::Interop::TypeName | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# 運算子 Windows::UI::Xaml::Interop::TypeName
可以從 `Platform::Type` 轉換為 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)。  
  
## 語法  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
## 傳回值  
 指定 `Platform::Type^` 時，則傳回 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)。  
  
## 備註  
 `TypeName` 是用來表示類型資訊的非語言相關 Windows 執行階段結構。[Platform::Type](../cppcx/platform-type-class.md) 則是 C\+\+ 專屬，並且無法跨應用程式二進位介面 \(ABI\) 傳遞。 以下是 `TypeName` 其中一種在 [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) 函式內的用法：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## 範例  
 下一個範例顯示如何在 `TypeName` 和 `Type` 之間轉換。  
  
```  
  
// Convert from Type to TypeName Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid); // Convert back from TypeName to Type Type^ tx2 = (Type^)(tn);  
  
```  
  
## .NET Framework 對等用法  
 .NET Framework 程式會將 `TypeName` 視為 [System.Type](assetId:///System.Type?qualifyHint=False&amp;autoUpgrade=True)。  
  
## 需求  
  
## 請參閱  
 [operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)   
 [Platform::Type 類別](../cppcx/platform-type-class.md)