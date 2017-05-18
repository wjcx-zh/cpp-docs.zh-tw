---
title: "加入 ATL OLE DB 消費者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c7202444e1b3aa473060df359dbeb8a8668f65f4
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="adding-an-atl-ole-db-consumer"></a>加入 ATL OLE DB 消費者
使用此精靈將 ATL OLE DB 取用者加入至專案。 ATL OLE DB 取用者包含 OLE DB 存取子類別和資料繫結的必要存取資料來源。 專案必須建立為 ATL COM 應用程式，或包含 （其 ATL OLE DB 消費者精靈會自動新增） 的 ATL 支援的 MFC 或 Win32 應用程式。  
  
 **請注意**加入 MFC 專案的 OLE DB 取用者。 如果您這樣做，ATL OLE DB 消費者精靈會將必要的 COM 支援加入至專案。 這是假設您建立 MFC 專案，當您選取**ActiveX 控制項**核取方塊 (在**進階功能**MFC 專案的應用程式精靈頁面)，其預設為核取。 選取此選項可確保應用程式呼叫**CoInitialize**和**CoUninitialize**。 如果您未選取**ActiveX 控制項**當您建立 MFC 專案，您需要呼叫**CoInitialize**和**CoUninitialize**主要程式碼中。  
  
### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>若要加入到專案中的 ATL OLE DB 消費者  
  
1.  在 類別檢視，以滑鼠右鍵按一下專案。 在捷徑功能表，按一下 **新增**然後按一下 **加入類別**。  
  
2.  在 Visual c + +] 資料夾中，按兩下**ATL OLE DB 消費者**圖示或選取它，然後按一下 [**開啟**。  
  
     ATL OLE DB 消費者精靈隨即開啟。  
  
3.  定義設定中所述[ATL OLE DB 消費者精靈](../../atl/reference/atl-ole-db-consumer-wizard.md)。  
  
4.  按一下 **完成**關閉精靈。 新建立的 OLE DB 消費者程式碼將會插入您的專案中。  
  
## <a name="see-also"></a>另請參閱  
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)


