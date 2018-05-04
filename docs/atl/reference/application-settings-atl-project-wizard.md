---
title: 應用程式設定，ATL 專案精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.atl.com.appset
dev_langs:
- C++
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47fbf95451834e5f8c41e8b6d7e5af7a9746bb85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="application-settings-atl-project-wizard"></a>應用程式設定, ATL 專案精靈
使用**應用程式設定**設計基本功能並將新的 ATL 專案在 ATL 專案精靈 頁面。  
  
## <a name="server-type"></a>伺服器類型  
 選擇三種伺服器類型之一：  
  
 **動態連結程式庫 (DLL)**  
 選取即可建立同處理序伺服器。  
  
 **可執行檔 (EXE)**  
 選取即可建立本機的跨處理序伺服器。 這個選項不允許支援 MFC 或 COM + 1.0。 它不允許合併 proxy/stub 程式碼。  
  
 **服務 (EXE)**  
 選取即可建立 Windows 啟動時，會在背景中執行的 Windows 應用程式。 此選項不允許支援 MFC 或 COM + 1.0，或不允許合併 proxy/stub 程式碼。  
  
## <a name="additional-options"></a>其他選項  
  
> [!NOTE]
>  所有其他選項都適用於 DLL 專案。  
  
 **允許合併 proxy/stub 程式碼**  
 選取**允許合併 proxy/stub 程式碼**核取方塊，以便於需要封送處理介面時。 此選項會將在相同可執行檔做為伺服器的 MIDL 產生 proxy 和虛設常式程式碼。  
  
 **MFC 支援**  
 選取即可指定您的物件包含 MFC 支援。 這個選項會連結您的專案到 MFC 程式庫，讓您可以存取的任何類別及它們包含的功能。  
  
 **支援 COM + 1.0**  
 選取要修改專案的組建設定，以支援 COM + 1.0 元件。 除了標準的程式庫清單中，精靈會新增 COM + 1.0 元件特定的程式庫 comsvcs.lib  
  
 此外，mtxex.dll 是您的應用程式啟動時載入主機系統上的延遲。  
  
-   **支援元件登錄器**如果您的 ATL 專案包含 COM + 1.0 元件的支援，您可以設定這個選項。 元件的註冊機構可讓您取得的元件清單中，登錄元件，或取消登錄元件 （個別或全部） 的 COM + 1.0 物件。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [建立的 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

