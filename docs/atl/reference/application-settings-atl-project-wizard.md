---
title: 應用程式設定]、 [ATL 專案精靈 |Microsoft Docs
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
ms.openlocfilehash: dee20d07ff37024506ef925fd94363bf85ceb8bc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756882"
---
# <a name="application-settings-atl-project-wizard"></a>應用程式設定, ATL 專案精靈

使用**應用程式設定**ATL 專案的設計，並將基本的功能新增至新的 ATL 專案精靈 頁面。

## <a name="server-type"></a>伺服器類型

選擇其中一種伺服器類型：

**動態連結程式庫 (DLL)**  
選取即可建立同處理序伺服器。

**可執行檔 (EXE)**  
選取即可建立本機的跨處理序伺服器。 此選項不允許對 MFC 或 COM + 1.0 支援。 它不會不允許合併 proxy/stub 程式碼。

**服務 (EXE)**  
選取即可建立 Windows 啟動時，會在背景中執行的 Windows 應用程式。 此選項不允許支援 MFC 或 COM + 1.0，或不允許合併 proxy/stub 程式碼。

## <a name="additional-options"></a>其他選項

> [!NOTE]
>  所有其他選項都適用於僅限 DLL 專案。

**允許合併 proxy/stub 程式碼**  
選取 **允許合併 proxy/stub 程式碼**核取方塊，以便於需要封送處理介面時。 此選項將放在同一個可執行檔當做伺服器 MIDL 產生 proxy 和虛設常式的程式碼。

**MFC 支援**  
選取此選項，以指定您的物件，包含 MFC 支援。 此選項，將您的專案連結至 MFC 程式庫，讓您可以存取的任何類別和其所包含的函式。

**支援 COM + 1.0**  
選取此選項，即可修改專案組建設定，以支援 COM + 1.0 元件。 除了標準的程式庫清單中，精靈會新增 COM + 1.0 元件特有的程式庫 comsvcs.lib

颾魤 ㄛ mtxex.dll 是您的應用程式啟動時，主機系統上載入的延遲。

- **支援元件登錄器**如果 ATL 專案會包含 COM + 1.0 元件的支援，您可以設定此選項。 支援元件登錄器可讓您的 COM + 1.0 物件取得的元件清單、 登錄元件，或取消登錄元件 （個別或全部一次）。

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

