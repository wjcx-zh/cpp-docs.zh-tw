---
title: "CAtlServiceModuleT::Handler 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00158bbed5318d919c284b91cd651141a35bd441
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT::Handler 函式
`CAtlServiceModuleT::Handler`為服務控制管理員 (SCM) 呼叫以擷取服務的狀態，並賦予各種指示 （例如停止或暫停） 的常式。 SCM 會傳遞至作業碼`Handler`表示應該執行的服務。 預設 ATL 產生服務只會處理停止指令。 如果 SCM 通過 stop 指令，服務會告知 SCM 程式即將停止。 然後呼叫服務`PostThreadMessage`公佈至其本身的結束的訊息。 這樣會結束的訊息迴圈，服務會完全關閉。  
  
 若要處理的詳細指示，您需要變更`m_status`初始化中的資料成員`CAtlServiceModuleT`建構函式。 此資料成員會告知 SCM 来啟用服務已在 服務控制台應用程式中選取的按鈕。  
  
## <a name="see-also"></a>請參閱  
 [服務](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

