---
title: 建立 OLE DB 提供者 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f649b5b4c79c4148d0aed026b044485ca2b1eaa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-ole-db-provider"></a>建立 OLE DB 提供者
若要建立 OLE DB 提供者的建議的方式是使用精靈來建立 ATL COM 專案和提供者，然後修改使用 OLE DB 範本的檔案。 自訂您的提供者，您可以標記為註解的不必要的屬性，並加入選擇性的介面。  
  
 基本步驟如下：  
  
1.  若要建立基本專案檔和 ATL OLE DB 提供者精靈來建立提供者使用 ATL 專案精靈 (選取**ATL OLE DB 提供者**Visual c + + 資料夾中**加入類別**)。  
  
2.  修改中的程式碼`Execute`CMyProviderRS.h 中的方法。 如需範例，請參閱[讀取字串至 OLE DB 提供者](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。  
  
3.  編輯 MyProviderDS.h、 MyProviderSess.h 和 MyProviderRS.h 中的屬性對應。 精靈會建立包含可能會實作提供者的所有屬性的屬性對應。 瀏覽屬性對應，移除或註解您的提供者不需要支援的屬性。  
  
4.  更新 PROVIDER_COLUMN_MAP MyProviderRS.h 中可以找到。 如需範例，請參閱[儲存字串中 OLE DB 提供者](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。  
  
5.  當您準備好要測試您的提供者時，您可以藉由嘗試在提供者的列舉中尋找的提供者來進行測試。 例如在列舉中尋找的提供者的測試程式碼的詳細資訊，請參閱[CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)和[DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)範例或中的範例[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)。  
  
6.  加入您想要的任何其他介面。 如需範例，請參閱[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
    > [!NOTE]
    >  根據預設，精靈會產生 OLE DB 層級 0 相容的程式碼。 若要確保您的應用程式層級 0 相容，請勿從程式碼中移除任何精靈產生的介面。  
  
## <a name="see-also"></a>另請參閱  
 [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)