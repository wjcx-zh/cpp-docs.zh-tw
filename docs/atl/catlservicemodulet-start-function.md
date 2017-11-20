---
title: "CAtlServiceModuleT::Start 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs: C++
helpviewer_keywords: Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3eb7009e8092184effad5e1874297c8c04b213e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Start 函式
執行服務時， **_tWinMain**呼叫**CAtlServiceModuleT::WinMain**，接著呼叫`CAtlServiceModuleT::Start`。  
  
 `CAtlServiceModuleT::Start`設定陣列**SERVICE_TABLE_ENTRY**對應至其啟動函式的每個服務的結構。 這個陣列會再傳遞至 Win32 API 函式[StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324)。 理論上，一個 EXE 處理多個服務，且陣列可能有多個**SERVICE_TABLE_ENTRY**結構。 目前，不過，ATL 產生服務支援只有一個服務每個 EXE。 因此，陣列中有單一項目，其中包含服務名稱和**_ServiceMain**為啟動函式。 **_ServiceMain**是靜態成員函式的`CAtlServiceModuleT`呼叫非靜態成員函式`ServiceMain`。  
  
> [!NOTE]
>  失敗的**StartServiceCtrlDispatcher**連接到服務控制管理員 (SCM) 情況，可能表示不以服務執行程式。 在此情況下，程式會呼叫`CAtlServiceModuleT::Run`直接，讓程式可以做為本機伺服器執行。 如需為本機伺服器執行程式的詳細資訊，請參閱[偵錯秘訣](../atl/debugging-tips.md)。  
  
## <a name="see-also"></a>另請參閱  
 [服務](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

