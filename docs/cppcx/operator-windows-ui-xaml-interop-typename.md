---
title: 運算子 Windows::UI::Xaml::Interop::TypeName |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50c7b6a8e62aa957c54f66ebaf87fcd86df458fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199339"
---
# <a name="operator-windowsuixamlinteroptypename"></a>運算子 Windows::UI::Xaml::Interop::TypeName
可讓從轉換`Platform::Type`要[Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>傳回值  
 傳回[Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)時指定`Platform::Type^`。  
  
### <a name="remarks"></a>備註  
 `TypeName` 是用來表示類型資訊的非語言相關 Windows 執行階段結構。 [Platform::Type](../cppcx/platform-type-class.md) 則是 C++ 專屬，並且無法跨應用程式二進位介面 (ABI) 傳遞。 以下是使用一`TypeName`，請在[Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx)函式：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>範例  
 下一個範例顯示如何在 `TypeName` 和 `Type`之間轉換。  
  
```  
  
// Convert from Type to TypeName  
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 .NET Framework 程式會將 `TypeName` 視為 [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)。  
  
### <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type 類別](../cppcx/platform-type-class.md)