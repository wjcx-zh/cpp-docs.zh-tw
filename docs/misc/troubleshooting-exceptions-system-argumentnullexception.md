---
title: "疑難排解例外狀況：System.ArgumentNullException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ArgumentNullException 類別"
ms.assetid: 5f21413c-d997-47c6-9b06-3d85a719d51b
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ArgumentNullException
當 null 參考 \(在 Visual Basic 中為 <xref:System.ArgumentNullException> \) 傳遞至不接受 null 參考做為有效引數的方法時，就會擲回 `Nothing` 例外狀況。  
  
## 相關秘訣  
 **檢查引數以確認不是 null \(在 Visual Basic 中為 Nothing\)。**  
 null 參考是一種不存在物件的參考，這通常是因為該物件未以程式的方式建立執行個體。  
  
## 備註  
 <xref:System.ArgumentNullException> 的行為與 <xref:System.ArgumentException> 相同。 這樣的安排方式，是為了讓應用程式程式碼能區分由 null 引數造成的例外狀況，以及非 null 引數所造成的例外狀況。 如需非 null 引數所造成的錯誤，請參閱[疑難排解例外狀況：System.ArgumentOutOfRangeException](../misc/troubleshooting-exceptions-system-argumentoutofrangeexception.md)。  
  
## 請參閱  
 <xref:System.ArgumentNullException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)