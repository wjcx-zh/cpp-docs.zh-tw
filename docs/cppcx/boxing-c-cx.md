---
title: Boxing (C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ed67496189388b869d7d9491ac4baad3de810ca
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203588"
---
# <a name="boxing-ccx"></a>Boxing (C++/CX)
*Boxing*這類包裝實值類型變數[Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)— 或基本純量類型，例如`int`— 在 ref 類別變數傳遞至採用的方法時[Platform:: object ^](../cppcx/platform-object-class.md)作為其輸入類型。  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>傳遞實值類型給 Object^ 參數  
 雖然您不需要明確將 Box 變數，以傳遞給 [Platform::Object^](../cppcx/platform-object-class.md)類型的方法參數，但是當您擷取先前已 Box 的值時，您必須明確轉換回原始類型。  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>使用 platform:: ibox\<T > 以支援可為 null 的實值型別  
 C# 和 Visual Basic 支援可為 null 的實值類型概念。 在 C + + /CX 中，您可以使用`Platform::IBox<T>`類型公開支援可為 null 的實值型別參數的公用方法。 下列範例顯示 C + + /CX 的公用方法，當 C# 呼叫端傳遞 null 給其中一個引數會傳回 null。  
  
 [!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]  
  
 在 C# XAML 用戶端中，您可以如下使用：  
  
```  
  
// C# client code  
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();  
    int? a = null;  
    int? b = 5;  
    var result = obj.Multiply(a,b); //result = null  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [類型系統 (C++/CX)](../cppcx/type-system-c-cx.md)   
 [轉型 (C + + /CX)](../cppcx/casting-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)