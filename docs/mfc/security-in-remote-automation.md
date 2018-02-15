---
title: "Remote Automation 中的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- AllowRemoteActivation [MFC]
- Remote Automation [MFC], security
- activating objects [MFC]
- security [MFC]
- Automation objects [MFC], security options
- object activation [MFC]
- security [MFC], Remote Automation
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e535fac6330d6268629e8e3681fec47c7b0d65d3
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="security-in-remote-automation"></a>Remote Automation 中的安全性
Remote Automation 支援基本層級的安全性，可讓伺服器應用程式撰寫者 (或其系統管理員) 指定可以什麼方式遠端啟動特定物件。 在指定系統上的所有自動化物件可能全域設定為「不允許遠端啟用」或「允許遠端啟用」。 此外，通常會提供個別物件這類功能。 Remote Automation 在每個物件的登錄設定中，使用金鑰**AllowRemoteActivation**，以決定給定的伺服器是否可遠端啟用。 如果全系統設定使用此模式，則登錄中的每個物件可能會指派這個機碼，而每一個的個別狀態可能會適當地設定為 [是] 或 [否]。  
  
 如果伺服器系統執行的是 Windows NT 或 Windows 2000，則允許替代形式的安全性。 在此情況中，Remote Automation 使用 NT 存取控制清單 (ACL) 來指定哪些使用者或哪些使用者群組可遠端啟動指定的伺服器。  
  
 請注意，安全性選項會套用至整個物件；無法在該物件上設定特定介面的屬性或者個別的屬性或方法。  
  
 所有安全性選項可透過 Remote Automation Connection (RAC) 管理員設定。  
  
## <a name="see-also"></a>請參閱  
 [Remote Automation](../mfc/remote-automation.md)

