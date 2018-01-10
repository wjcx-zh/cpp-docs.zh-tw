---
title: "使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: AUTOCLIK sample [MFC]
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 791655047eaf07732e1e006e8cc3ea8e7dec4727
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="running-remote-automation-using-autoclik-and-autodriv"></a>使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation
AUTOCLIK 是一個簡易的 Automation 伺服器範例應用程式，您可以用來作為深入了解 Automation 的基礎。 AUTODRIV 範例是一個驅動 AUTOCLIK 的簡易 Automation 用戶端應用程式。 您可以使用它們來示範 Remote Automation。  
  
#### <a name="to-install-autoclikexe-on-two-machines-and-drive-it-using-remote-automation"></a>使用 Remote Automation 在兩台電腦上安裝 AUTOCLIK.EXE 並且予以驅動  
  
1.  安裝[AUTOCLIK](../visual-cpp-samples.md)範例應用程式到開發電腦上的。  
  
2.  建置 AUTOCLIK.EXE。  
  
3.  獨立執行 AUTOCLIK.EXE 再將其關閉。 這會將其註冊為 Automation 伺服程式。  
  
4.  將 AUTOCLIK.EXE 複製到遠端電腦上，遠端執行該檔案，然後關閉。  
  
5.  在本機電腦上執行 AUTODRIV.EXE 並確認執行時會啟動 AUTOCLIK.EXE。 若要進一步了解 AUTODRIV。EXE，請參閱[AUTOCLIK](../visual-cpp-samples.md)。  
  
6.  在遠端電腦上，啟動 AUTMGR32.EXE (Automation 管理員)。  
  
7.  在遠端電腦上，啟動 RACMGR32.EXE (Remote Automation 連線管理員)。  
  
8.  在 Remote Automation 連接管理員 」 中，選取 AutoClik.Document **OLE 類別**清單。  
  
9. 選擇從系統安全性原則**用戶端存取**索引標籤，以授與 AutoClik.Document 的用戶端存取。  
  
10. 在本機電腦上啟動由於 RACMGR32。EXE 和選取 AutoClik.Document **OLE 類別**清單。  
  
11. 從**伺服器連接**索引標籤上，選擇 遠端電腦和適當的網路通訊協定的網路位址。  
  
12. 與中選取 AutoClik.Document 仍然**OLE 類別**清單方塊中，選擇**遠端**命令`Register`功能表。  
  
13. 如果您想要使用 Visual Basic 而非 MFC 用戶端，請在本機電腦上執行 AUTODRIV.EXE 或對等的 AUTOCLIK.MAK Visual Basic 專案。  
  
 在遠端電腦上，現在應該可以看到 AUTOCLIK 執行本機用戶端起始的命令。  
  
## <a name="see-also"></a>請參閱  
 [Remote Automation](../mfc/remote-automation.md)

