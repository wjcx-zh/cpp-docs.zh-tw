---
title: "在專案層級於 &#39;&lt;完整容器名稱&gt;&#39; 匯入 &#39;&lt;完整項目名稱&gt;&#39; 時發生錯誤：&lt;錯誤訊息&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在專案層級於 &#39;&lt;完整容器名稱&gt;&#39; 匯入 &#39;&lt;完整項目名稱&gt;&#39; 時發生錯誤：&lt;錯誤訊息&gt;
陳述式會存取定義在其他組件中的程式設計項目，但沒有該組件的專案參考。  
  
 例如，您的程式碼可能會使用限定性條件字串 `otherNamespace.otherClass.desiredEnumeration` 存取名為 `desiredEnumeration` 的列舉。 如果編譯器在您的專案參考中找不到 `otherNamespace.otherClass`，就會產生此錯誤。  
  
 **錯誤 ID︰**BC30797  
  
### 更正這個錯誤  
  
1.  請確定程式設計項目的限定性條件字串中的每個項目拼字正確。  
  
2.  請確定您的專案具有對定義所需程式設計項目之組件的參考。  
  
3.  請參閱錯誤訊息，並採取適當的動作。  
  
## 請參閱  
 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)