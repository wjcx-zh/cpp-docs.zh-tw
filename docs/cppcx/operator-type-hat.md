---
title: 運算子 Type ^ |Microsoft 文件
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c0900da889e5bf9e8629349593ffce7740a1cf0
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="operator-type"></a>運算子 Type^
可以從 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) 轉換為 `Platform::Type`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
```  
  
### <a name="return-value"></a>傳回值  
 指定 `Platform::Type` Windows::UI::Xaml::Interop::TypeName [時，則傳回](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)。  
  
### <a name="remarks"></a>備註  
 `TypeName` 是用來表示類型資訊的非語言相關 Windows 執行階段結構。 [Platform::Type](../cppcx/platform-type-class.md) 則是 C++ 專屬，並且無法跨應用程式二進位介面 (ABI) 傳遞。 以下是 `TypeName`其中一種在 [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) 函式內的用法：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>範例  
 下一個範例顯示如何在 `TypeName` 和 `Type`之間轉換。  
  
```  
  
// Convert from Type to TypeName  
TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 .NET Framework 程式會將 `TypeName` 視為 [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)。  
  
### <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type 類別](../cppcx/platform-type-class.md)