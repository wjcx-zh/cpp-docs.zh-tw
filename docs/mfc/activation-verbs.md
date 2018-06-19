---
title: 啟用： 動詞命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c484231eb87144a6546ff2b8b7061a5339820ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331070"
---
# <a name="activation-verbs"></a>啟用：動詞命令
本文說明在 OLE 中的角色主要和次要動詞播放[啟用](../mfc/activation-cpp.md)。  
  
 通常，按兩下內嵌項目可以讓使用者編輯它。 不過，某些項目未運作這種方式。 比方說，按兩下 錄音機 」 應用程式建立的項目不會開啟伺服器在不同的視窗。相反地，它會播放聲音。  
  
 此行為差異的原因是 錄音機 」 項目有不同 「 主要動作 」。 主要的動詞命令是在使用者按兩下 OLE 項目時所執行的動作。 對於大部分的 OLE 項目類型，主要的動詞命令是編輯、 啟動建立此項目的伺服器。 對於某些類型的項目，例如 錄音機 」 項目，主要的動詞命令是播放。  
  
 許多 OLE 項目類型支援只有一個動詞命令，並編輯是最常見的原因。 不過，某些項目類型支援多個動詞命令。 例如，項目支援錄音機 」 編輯以次要動作。  
  
 常用的另一個動作會開啟。 Open 動詞等同於編輯，但伺服器應用程式會在個別視窗中啟動。 容器應用程式或伺服器應用程式不支援就地啟用時，應該使用這個動詞命令。  
  
 必須透過子功能表命令叫用主動作以外的任何動作，在選取項目。 此子功能表包含項目所支援的動詞命令，並通常由達成*typename* **物件**命令**編輯**功能表。 如需有關詳細*typename* **物件**命令，請參閱文章[功能表和資源： 容器新增](../mfc/menus-and-resources-container-additions.md)。  
  
 伺服器應用程式支援的動詞命令會列出在 Windows 系統註冊資料庫。 如果您的伺服器應用程式撰寫與 Mfc 程式庫，它將會在伺服器啟動時自動註冊所有動詞命令。 如果沒有，您應該在伺服器應用程式的初始設定階段期間進行註冊。 如需詳細資訊，請參閱文章[註冊](../mfc/registration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [啟用](../mfc/activation-cpp.md)   
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)

