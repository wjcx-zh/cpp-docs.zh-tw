---
title: "Calling C++ Code from DHTML | Microsoft Docs"
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
  - "DHTML, calling C++ code from"
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Calling C++ Code from DHTML
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DHTML 控制項容器中可以裝載 \(Host\)，例如測試容器或 Internet Explorer。  如需如何存取測試容器的詳細資訊，請參閱 [測試屬性和事件會和測試容器](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
 使用一般控制項介面，裝載控制項的容器與控制項溝通。  DHTML 使用並加上「結尾進行通訊的 UI 與您的 C\+\+ 程式碼和您的 HTML 資源分派介面。  在 [修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)作法，您可以將這些不同的介面所呼叫的方法。  
  
 若要查看呼叫 C\+\+ 的範例，請從 DHTML 使用 ATL 控制項精靈的 [建立 DHTML 控制項](../atl/creating-an-atl-dhtml-control.md) 程式碼並檢視程式碼在標頭檔中並以 HTML 檔案。  
  
## 宣告在標頭檔中瀏覽器方法  
 若要叫用來自 DHTML UI 的 C\+\+ 方法，您必須將方法加入至控制項的 UI 介面。  例如， ATL 控制項精靈所建立的標頭檔包含 C\+\+ 方法 `OnClick`，是由精靈產生的控制項的 UI 介面的成員。  
  
 檢查控制項的 .h 檔案的 `OnClick` :  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/CPP/calling-cpp-code-from-dhtml_1.h)]  
  
 第一個參數， `pdispBody`，是指向主體物件的分派介面。  第二個參數， `varColor`，可用來將色彩套用至控制項。  
  
## 呼叫 HTML 檔案的 C\+\+ 程式碼  
 當您宣告在標頭檔中瀏覽器方法，您可以叫用方法從 HTML 檔案。  在 HTML 檔案的事項 ATL 控制項精靈將三個視窗分派方法:分派訊息變更控制項的背景色彩的三 `OnClick` 方法。  
  
 檢查某個 HTML 檔案的方法:  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 做為按鈕標記的一部分，在上述 HTML 程式碼，視窗外部方法， `OnClick`，呼叫。  方法有兩個參數: `theBody`，參考 HTML 文件主體和 `"red"`，表示控制項的背景色彩會變更為紅色，當按一下按鈕。  下列標記的 `Red` 是按鈕的標籤。  
  
 請參閱 [修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md) 如需提供自訂的方法的詳細資訊。  請參閱 [識別 DHTML 控制專案的項目。](../atl/identifying-the-elements-of-the-dhtml-control-project.md) 有關 HTML 檔案的詳細資訊。  
  
## 請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)