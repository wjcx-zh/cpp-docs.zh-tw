---
title: 建立 OLE DB 提供者 |Microsoft Docs
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
ms.openlocfilehash: 5de304b7a21c47af18b8b753d6de704ef2473c5f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338788"
---
# <a name="creating-an-ole-db-provider"></a>建立 OLE DB 提供者
建立 OLE DB 提供者的建議的方式是使用精靈來建立的 ATL COM 專案和提供者，然後修改使用 OLE DB 範本的檔案。 自訂您的提供者後，您可以標記為註解不必要的屬性，並新增選擇性的介面。  
  
 基本步驟如下：  
  
1.  若要建立基本專案檔和 ATL OLE DB 提供者精靈 來建立提供者使用 ATL 專案精靈 (選取**ATL OLE DB 提供者**Visual c + + 資料夾中**加入類別**)。  
  
2.  修改中的程式碼`Execute`CMyProviderRS.h 中的方法。 如需範例，請參閱[讀取字串至 OLE DB 提供者](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。  
  
3.  編輯 MyProviderDS.h、 MyProviderSess.h 和 MyProviderRS.h 中的屬性對應。 此精靈會建立包含提供者可能會實作的所有屬性的屬性對應。 瀏覽屬性對應，並移除或註解您的提供者不需要支援的屬性。  
  
4.  更新 PROVIDER_COLUMN_MAP，可以在 MyProviderRS.h 中找到。 如需範例，請參閱[儲存字串中的 OLE DB 提供者](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。  
  
5.  當您準備好測試您的提供者時，您可以嘗試尋找的提供者在提供者的列舉型別來測試。 例如尋找提供者列舉中的測試程式碼的詳細資訊，請參閱[CATDB](http://msdn.microsoft.com/003d516b-2bf6-444e-8be5-4ebaa0b66046)並[DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832)範例或中的範例[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)。  
  
6.  新增您想要的任何其他介面。 如需範例，請參閱[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
    > [!NOTE]
    >  根據預設，精靈會產生為 OLE DB 層級 0 相容的程式碼。 若要確保您的應用程式層級 0 相容，請不要移除精靈所產生的任何的介面程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [CATDB](http://msdn.microsoft.com/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832)