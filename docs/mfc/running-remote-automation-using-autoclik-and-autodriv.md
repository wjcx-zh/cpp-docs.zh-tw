---
title: "使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation | Microsoft Docs"
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
  - "AUTOCLIK 範例 [MFC]"
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以是您可以使用做為基底進一步了解遠端自動化的簡單 Automation 伺服程式應用程式。  AUTODRIV 範例是一個驅動 AUTOCLIK 的簡易 Automation 用戶端應用程式。  您可以使用它們來示範遠端自動化。  
  
#### 使用遠端自動化，安裝在兩台電腦的 AUTOCLIK.EXE 和巡覽它  
  
1.  安裝在開發電腦上的 [AUTOCLIK](../top/visual-cpp-samples.md) 範例應用程式。  
  
2.  建置 AUTOCLIK.EXE。  
  
3.  執行 AUTOCLIK.EXE 無關的方式將其關閉。  這會註冊為 Automation 伺服程式。  
  
4.  複製 AUTOCLIK.EXE 對遠端電腦上，執行該檔案，然後關閉檔案。  
  
5.  在本機電腦上 AUTODRIV.EXE 並確認執行啟動 AUTOCLIK.EXE。  如需詳細資訊 AUTODRIV.EXE，請參閱 [AUTOCLIK](../top/visual-cpp-samples.md)。  
  
6.  在遠端機器上，啟動 AUTMGR32.EXE \(Automation 管理員\)。  
  
7.  在遠端機器上，啟動 RACMGR32.EXE \(Remote Automation 連接管理員\)。  
  
8.  在遠端自動化連接管理員 **OLE Classes** ，從清單中選取 AutoClik.Document。  
  
9. 從 **Client Access** 選項選取系統安全性原則授與 AutoClik.Document 的用戶端存取。  
  
10. 在本機電腦上，啟動 RACMGR32.EXE\] AutoClik.Document 從 **OLE Classes** 清單。  
  
11. 從 **Server Connection** 選項，請選擇遠端電腦的網路位址和適當的網路通訊協定。  
  
12. 使用在 **OLE Classes** 清單方塊仍選取的 AutoClik.Document，選取 `Register` 功能表中選擇 **Remote** 命令。  
  
13. 在本機電腦上執行的 AUTODRIV.EXE 或對等的 AUTOCLIK.MAK Visual Basic 專案要使用 Visual Basic，而非 MFC，用戶端。  
  
 在遠端機器上，現在應該可以看到 AUTOCLIK 執行命令的您啟始本機用戶端。  
  
## 請參閱  
 [Remote Automation](../mfc/remote-automation.md)