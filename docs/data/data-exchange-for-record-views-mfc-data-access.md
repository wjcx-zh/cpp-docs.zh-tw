---
title: "資料錄檢視 （MFC 資料存取） 的資料交換 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1db5adaab66fec2b587f7a15005caa3a9374ff12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>記錄檢視的資料交換 (MFC 資料存取)
當您使用[加入類別](../mfc/reference/adding-an-mfc-odbc-consumer.md)資料錄檢視的對話方塊範本資源中的控制項對應至資料錄集的欄位，架構會管理雙向的資料交換 — 從記錄集到控制項和控制項至資料錄集。 使用 DDX 機制意味著您不需要自行撰寫程式碼以來回傳輸資料。  
  
 資料錄檢視的 DDX 可搭配[RFX](../data/odbc/record-field-exchange-rfx.md)類別的資料錄集的`CRecordset`(ODBC)。  RFX 目前記錄的資料來源和資料錄集物件的欄位資料成員之間移動資料。 DDX 會將資料，從欄位資料成員移到表單中的控制項。 這種組合會在一開始以及使用者在記錄間移動時，填滿表單控制項。 它也可以將更新的資料移動回記錄集，然後移到資料來源。  
  
 下圖顯示資料錄檢視的 DDX 及 RFX 之間的關聯性。  
  
 ![對話方塊 &#45; 資料交換及記錄 &#45; 欄位交換](../data/media/vc37xt1.gif "vc37xt1")  
對話方塊資料交換及記錄欄位交換  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。 如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 (RFX)](../data/odbc/record-field-exchange-rfx.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄檢視 （MFC 資料存取）](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)