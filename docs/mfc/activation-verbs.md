---
title: "啟用：動詞命令 | Microsoft Docs"
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
  - "啟用 [C++], 動作"
  - "編輯動詞命令"
  - "OLE [C++], 啟動"
  - "OLE [C++], 編輯"
  - "OLE 啟動"
  - "主動詞命令"
  - "動作"
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 啟用：動詞命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明主要的角色，次要動詞命令會在 OLE [啟動](../mfc/activation-cpp.md)。  
  
 通常，按兩下內嵌項目可讓使用者編輯它。  不過，某些項目不會以這種方式。  例如，按兩下項目建立合理記錄之應用程式不會在另一個視窗中伺服器;相反地，會播放音效。  
  
 這個行為差異的原因是合理記錄的項目已具有不同的「master」的動詞命令。當使用者按兩下 OLE 項目時，主要動詞命令是執行的動作。  對於 OLE 項目的大部分類型，主要動詞命令是編輯，啟動伺服器建立項目。  如需項目的型別參數，例如合理記錄成員項目，主要動詞命令是播放。  
  
 OLE 項目的許多型別只支援一個動詞命令，，和編輯是最常用的一個。  不過，項目的一些型別支援多個動詞命令。  例如，合理記錄成員項目支援編輯為次要動詞命令。  
  
 常用的另一個動詞命令是開啟的。  開啟動詞命令與編輯相同，不同的是，伺服器應用程式在不同視窗中啟動。  此動詞命令，在容器應用程式或伺服器應用程式不支援就地啟動時，應該使用。  
  
 當項目被選取時，必須將子功能表命令叫用刪除主要動詞命令之外的所有動詞命令。  這個功能表包含項目支援的所有動詞命令以及 **Edit** 功能表的 *typename* **Object** 命令通常到達。  如需 *typename* **Object** 命令的詳細資訊，請參閱本文件的 [功能表和資源:加入容器](../mfc/menus-and-resources-container-additions.md)。  
  
 動詞命令的伺服器應用程式支援在 Windows 系統註冊資料庫清單。  如果您的伺服器應用程式會使用 MFC 程式庫，它會自動註冊所有動詞命令，在伺服器上啟動。  在伺服器應用程式的初始化階段，則為，否則您應該註冊它們。  如需詳細資訊，請參閱文件 [註冊](../mfc/registration.md)。  
  
## 請參閱  
 [啟用](../mfc/activation-cpp.md)   
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)