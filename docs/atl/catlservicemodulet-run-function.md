---
title: "CAtlServiceModuleT::Run 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs: C++
helpviewer_keywords: ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ff3efe9298b7a2c11e7f83ef58640b2947519b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT::Run 函式
**執行**包含呼叫`PreMessageLoop`， `RunMessageLoop`，和`PostMessageLoop`。 之後，呼叫`PreMessageLoop`先儲存服務的執行緒識別碼。 服務會使用這個識別碼來自動關閉傳送**WM_QUIT**訊息使用 Win32 API 函式[PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946)。  
  
 `PreMessageLoop`然後呼叫`InitializeSecurity`。 根據預設，`InitializeSecurity`呼叫[CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736)與安全性描述元設定為 NULL，這表示任何使用者可以對您物件的存取。  
  
 如果您不想要指定自己的安全性服務，會覆寫`PreMessageLoop`和不要呼叫`InitializeSecurity`，COM 然後會判斷登錄的安全性設定。 設定登錄設定的簡便方法是使用[DCOMCNFG](../atl/dcomcnfg.md)本章節稍後所討論的公用程式。  
  
 安全性指定之後，物件是使用 COM 註冊，使新的用戶端可以連線到程式。 最後，程式執行，而且程式會進入訊息迴圈會告知服務控制管理員 (SCM)。 直到它發出一個結束的訊息在服務關閉時，仍繼續執行程式。  
  
## <a name="see-also"></a>請參閱  
 [服務](../atl/atl-services.md)   
 [CSecurityDesc 類別](../atl/reference/csecuritydesc-class.md)   
 [CSid 類別](../atl/reference/csid-class.md)   
 [CDacl 類別](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

