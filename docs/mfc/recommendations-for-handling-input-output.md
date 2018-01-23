---
title: "處理輸入輸出的建議 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc7fbb58aa1ac85c185756eb336737cbaf33a48e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recommendations-for-handling-inputoutput"></a>處理輸入/輸出的建議
無論您使用以檔案為基礎的 I/O 或不是取決於您如何回應下列決策樹狀結構中的問題：  
  
 **您的應用程式中的主資料存放在磁碟檔案中**  
  
-   [是]，主要資料位於磁碟檔案：  
  
     **沒有應用程式整個檔案讀取到記憶體上開啟檔案，並將整個檔案寫回至磁碟上儲存檔案嗎**  
  
    -   是: 這是預設的 MFC 文件大小寫。 使用**CDocument**序列化。  
  
    -   否： 這通常是交易式更新檔案的大小寫。 在您更新每個交易為基礎的檔案，並不需要**CDocument**序列化。  
  
-   否，主要資料不會存放在磁碟檔案：  
  
     **沒有資料會位於 ODBC 資料來源嗎**  
  
    -   [是]，資料所在的 ODBC 資料來源中：  
  
         使用 MFC 資料庫支援。 此案例的標準 MFC 實作包含`CDatabase`物件，如本文所討論[MFC： 使用具有文件和檢視的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)。 應用程式也可能會讀取並撰寫的輔助檔案 — 應用程式精靈 」 資料庫檢視和檔案支援 」 選項的目的。 在此情況下，您會使用序列化輔助檔案。  
  
    -   否，資料不會位於 ODBC 資料來源。  
  
         此案例的範例： 資料存放在非 ODBC DBMS;透過其他機制，例如 OLE 或 DDE 讀取資料。  
  
         在這種情況下，您不會使用序列化，並且您的應用程式將不會有開啟及儲存功能表項目。 您仍可能會想要使用**CDocument**作為住家基底，就如同 MFC ODBC 應用程式會使用文件來儲存`CRecordset`物件。 但您不會使用架構的預設檔案開啟/儲存文件序列化。  
  
 若要支援開啟、 儲存，並將儲存為命令，在 [檔案] 功能表上，此架構會提供文件序列化。 序列化讀取和寫入資料，包括物件衍生自類別`CObject`，到永久儲存體，通常是磁碟檔案。 序列化簡單易用，並提供許多您的需求，但它可能不適合在許多資料存取應用程式。 資料存取應用程式通常會更新每個交易為基礎的資料。 他們會更新受影響的交易，而非讀取和寫入整個資料檔一次記錄。  
  
 如需序列化資訊，請參閱[序列化](../mfc/serialization-in-mfc.md)。  
  
## <a name="see-also"></a>請參閱  
 [序列化︰序列化和資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)
