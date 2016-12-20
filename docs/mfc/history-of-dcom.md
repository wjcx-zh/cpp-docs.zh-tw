---
title: "DCOM 的歷史 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DCOM"
  - "DCOM, 關於 DCOM"
  - "Remote Automation, DCOM"
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DCOM 的歷史
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當 Automation 在 1993 年逐步中首次引入，它可以只能在執行在相同的電腦上的應用程式之間。  不過，，因為，也就是說，它具有共用基底和其他 OLE 相同 COM \(或元件物件模型 \(Component Object Model，COM\)，一定要將它變成「遠端」，當更新 COM 包括遠端功能。  同時也規劃轉換從本機作業加入至分散式作業單純地將需要對現有程式碼的幾乎不會變更。  
  
 因此哪些遠端」方法?  區域 COM 元件介面的消費者在電腦填入並執行和該介面相同的提供者。  例如， Microsoft Visual Basic 可以控制 Microsoft Excel 的複本桌上型電腦上，不過，它不能讓 Excel 執行在另一部電腦上。  分散式 COM 的開發，介面的消費者不再需要使用電腦和介面提供者所執行的一樣。  
  
 一旦 COM 符合了在網路上的工作，然後未繫結至本機執行模型 \(的所有介面某些介面對本機電腦功能的適當信任，例如方法的裝置內容控制代碼當做參數傳遞\) 將會發出的功能的繪圖介面。  介面消費者會要求特定介面;該介面可以由目標作業執行個體提供 \(或\) 會在不同的電腦。  在 COM 中發行機制將連接由消費者至提供者，在這種情況下消費者所進行的方法呼叫將會出現在提供者端點，則會執行。  任何傳回值則傳回給消費者。  實際上，發行動作是透明的消費者和提供者。  
  
 這類各種 COM 現在存在。  DCOM \(「分散式 COM\) 隨附於 Windows NT 版本從 4.0 版和包含啟動 Windows 2000。  從 1996 年末，它也為 Windows 9x 可用。  在這兩種情況下，存取包含一組取代和其他 DLL，與某些公用程式，提供本機和遠端 COM 功能。  因此現在是 Win32 架構的平台上一個程式組件和經過一段時間後即可在其他平台上由其他組織。  
  
## 本章節內容  
 [遠端自動化位置符合?](../mfc/where-does-remote-automation-fit-in-q.md)  
  
 [遠端自動化提供為何?](../mfc/what-does-remote-automation-provide-q.md)  
  
## 請參閱  
 [Remote Automation](../mfc/remote-automation.md)