---
title: "命令路由說明 |Microsoft 文件"
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
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24ac591005d5df6b18102d296352b8b2528ba839
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="command-routing-illustration"></a>命令路由說明
為了說明，請考慮來自 MDI 應用程式的 [編輯] 功能表中 [全部清除] 功能表項目的命令訊息。 假設這個命令的處理函式正好是應用程式的文件類別的成員函式。 以下是該命令在使用者選擇功能表項目後抵達其處理常式的方式：  
  
1.  主框架視窗首先會接收命令訊息。  
  
2.  主要 MDI 框架視窗讓目前作用中 MDI 子視窗有機會處理命令。  
  
3.  MDI 子框架視窗的標準路由路徑，會在檢查其本身的訊息對應之前，在命令處給予其檢視機會進行檢查。  
  
4.  該檢視會先檢查其本身的訊息對應，若找不到處理常式，便接著將命令路由到其相關的文件。  
  
5.  文件會檢查其訊息對應並尋找處理常式。 然後，呼叫此文件成員函式，路由隨即停止。  
  
 如果文件沒有處理常式，它會接著將命令路由到其文件範本。 然後，命令會回到檢視，接著回到框架視窗。 最後，框架視窗會檢查其訊息對應。 如果該檢查也失敗，命令便會路由回到主要 MDI 框架視窗，然後回到應用程式物件，也就是未處理命令的最終目的地。  
  
## <a name="see-also"></a>請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

