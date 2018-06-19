---
title: Boxing (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e47313f65c4129bbc6fbf0a7bfbf698eb092f9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086495"
---
# <a name="boxing-ccx"></a>Boxing (C++/CX)
將實值類型變數 (例如 *) 傳遞給使用* ) 或基本純量類型變數 (例如 [) 傳遞給使用](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)Boxing `int`作為其輸入類型的方法時， [Boxing](../cppcx/platform-object-class.md) 會將此變數包裝在 ref 類別中。  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>傳遞實值類型給 Object^ 參數  
 雖然您不需要明確將 Box 變數，以傳遞給 [Platform::Object^](../cppcx/platform-object-class.md)類型的方法參數，但是當您擷取先前已 Box 的值時，您必須明確轉換回原始類型。  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>使用 platform:: ibox\<T > 以支援可為 null 的實值類型  
 C# 和 Visual Basic 支援可為 null 的實值類型概念。 在 C + + /CX 中，您可以使用`Platform::IBox<T>`類型公開支援可為 null 的實值型別參數的公用方法。 下列範例顯示 C + + /CX 當 C# 呼叫端傳遞 null 給其中一個引數時傳回 null 的公用方法。  
  
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