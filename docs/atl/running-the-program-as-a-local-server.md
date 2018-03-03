---
title: "執行程式為本機伺服器 |Microsoft 文件"
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
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e398bfed0174e4ec2a262ea03076ed17881f900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="running-the-program-as-a-local-server"></a>為本機伺服器執行程式
如果以服務方式執行程式，是很方便，您可以暫時變更登錄，讓程式做為一般的本機伺服器執行。 只重新命名`LocalService`下您應用程式識別碼值`_LocalService`，並確定`LocalServer32`您 CLSID 機已正確設定。 (請注意，若要指定您的應用程式應在另一部電腦上執行使用 DCOMCNFG 重新命名您`LocalServer32`鍵`_LocalServer32`。)依本機伺服器會需要在啟動多個的幾秒鐘因為執行您的程式呼叫**StartServiceCtrlDispatcher**中`CAtlServiceModuleT::Start`需要幾秒鐘之前它就會失敗。  
  
## <a name="see-also"></a>請參閱  
 [偵錯提示](../atl/debugging-tips.md)

