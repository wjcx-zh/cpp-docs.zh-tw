---
title: "無法在此內容中存取 &#39;&lt;方法名稱&gt;&#39;，因為無法存取傳回類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36665"
  - "vbc36666"
  - "bc36666"
  - "vbc36665"
helpviewer_keywords: 
  - "BC36666"
  - "BC36665"
ms.assetid: 8f29eb7e-351f-486c-9d1f-3556cc11b7c5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在此內容中存取 &#39;&lt;方法名稱&gt;&#39;，因為無法存取傳回類型
您所呼叫的函式具有無法從呼叫陳述式存取的傳回類型。 例如，在下列程式碼中，從 `Main` 對 `PublicMethod` 的呼叫失敗，因為在 `TestClass` 類別中使用 `Private` 存取修飾詞宣告了傳回類型 `PrivateType`。 因此，可從中存取 `PrivateType` 的內容僅限於 `TestClass`。  
  
```vb#  
Class TestClass  
  
    Dim pT As New PrivateType  
  
    Private Class PrivateType  
    End Class  
  
    '' A corresponding error is returned in this line: 'PublicMethod   
    '' cannot expose 'PrivateType' in namespace 'ConsoleApplication1'   
    '' through class 'TestClass'.  
    'Public Function PublicMethod() As PrivateType  
    '    Return Nothing  
    'End Function  
  
End Class  
  
Module Module1  
  
    Sub Main()  
  
        Dim tc As TestClass  
        '' This error occurs here, because the data type returned by   
        '' PublicMethod()is declared Private in class TestClass and   
        '' cannot be accessed from here.  
        'Console.WriteLine(tc.PublicMethod())  
  
    End Sub  
  
End Module  
```  
  
 **錯誤 ID︰**BC36665 和 BC36666  
  
### 更正這個錯誤  
  
-   如果類型定義可供存取，請將存取修飾詞從 `Private` 變更為 `Public`。  
  
-   如果您可以存取此定義，請變更函式的傳回類型。  
  
-   撰寫傳回可存取之類型的方法或擴充方法。  
  
## 請參閱  
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)