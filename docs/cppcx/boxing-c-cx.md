---
title: "Boxing (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
caps.latest.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 12
---
# Boxing (C++/CX)
將實值類型變數 \(例如 [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)\) 或基本純量類型變數 \(例如 `int`\) 傳遞給使用 [Platform::Object^](../cppcx/platform-object-class.md) 作為其輸入類型的方法時，*Boxing* 會將此變數包裝在 ref 類別中。  
  
## 傳遞實值類型給 Object^ 參數  
 雖然您不需要明確將 Box 變數，以傳遞給 [Platform::Object^](../cppcx/platform-object-class.md) 類型的方法參數，但是當您擷取先前已 Box 的值時，您必須明確轉換回原始類型。  
  
 [!code-cpp[cx_boxing#01](../snippets/cpp/VS_Snippets_Misc/cx_boxing/cpp/class1.cpp#01)]  
  
### 使用 Platform::IBox\<T\> 支援可為 Null 的實值類型  
 C\# 和 Visual Basic 支援可為 null 的實值類型概念。 在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，您可以使用 `Platform::IBox<T>` 類型公開支援可為 null 的實值類型參數的公用方法。 下列範例示範當 C\# 呼叫端傳遞 null 給其中一個引數時，傳回 null 的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 公用方法。  
  
 [!code-cpp[cx_boxing#02](../snippets/cpp/VS_Snippets_Misc/cx_boxing/cpp/class1.h#02)]  
  
 在 C\# XAML 用戶端中，您可以如下使用：  
  
```  
  
// C# client code BoxingDemo.Class1 obj = new BoxingDemo.Class1(); int? a = null; int? b = 5; var result = obj.Multiply(a,b); //result = null  
  
```  
  
## 請參閱  
 [類型系統 \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [轉型 \(C\+\+\/CX\)](../cppcx/casting-c-cx.md)   
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)