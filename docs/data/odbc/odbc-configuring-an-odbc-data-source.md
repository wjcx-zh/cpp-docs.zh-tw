---
title: ODBC：設定 ODBC 資料來源
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
ms.openlocfilehash: 43d385bea34ba885b9ae0f8efb6109e6959c2383
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213131"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC：設定 ODBC 資料來源

若要將[資料來源](../../data/odbc/data-source-odbc.md)與您所開發的應用程式搭配使用，您必須使用 ODBC 管理員來設定它。 ODBC 系統管理員會在 Windows 登錄中持續追蹤可用的資料來源及其連接資訊。 使用 ODBC 管理員，在 [**資料來源**] 對話方塊中加入、修改和刪除資料來源，以及加入和刪除 ODBC 驅動程式。

> [!NOTE]
>  當您使用適用于 ODBC 存取的 MFC 資料存取物件（DAO）類別，以及使用 MFC ODBC 類別時，就會套用此資訊。

ODBC 管理員會隨著 Microsoft Foundation class （MFC）程式庫資料庫的支援自動安裝。 如需 ODBC 系統管理員程式的詳細資訊，請參閱[Odbc 系統管理員](../../data/odbc/odbc-administrator.md)和線上 Odbc API 參考說明系統。

如需有關如何撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式的詳細資訊，請[注意技術提示 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)<br/>
[ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)
