---
title: "不允許使用 Set | Microsoft Docs"
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
  - "vbrID387"
ms.assetid: 809f6768-7dd7-4632-b4dd-83856edfdb48
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不允許使用 Set
您嘗試要變更無法在執行階段設定其設定的屬性，或是只能在某些情況下設定其設定的屬性。 例如，您可能嘗試在執行階段變更表單的 `Appearance`、`ControlBox`、`MinButton` 或 `MaxButton` 屬性設定，或是您可能嘗試針對父功能表上最後一個剩餘可見的子功能表，將 `Visible` 屬性設為 `False`。  
  
### 更正這個錯誤  
  
1.  請檢查屬性，並判斷在哪些情況下可以設定屬性。  
  
## 請參閱  
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)