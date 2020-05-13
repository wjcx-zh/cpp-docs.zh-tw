---
title: ODBC：設定 ODBC 資料來源
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
ms.openlocfilehash: aaa69fd7e0b2b592cd7d5c4eff92f51d0ce5f680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367202"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC：設定 ODBC 資料來源

要將[資料源](../../data/odbc/data-source-odbc.md)與已開發的應用程式一起使用,必須使用ODBC管理員對其進行配置。 ODBC 管理員在 Windows 註冊表中追蹤可用數據源及其連接資訊。 使用 ODBC 管理員在 **「資料源」** 對話方塊中添加、修改和刪除數據來源,並添加和刪除 ODBC 驅動程式。

> [!NOTE]
> 當您使用 MFC 數據存取物件 (DAO) 類別進行 ODBC 存取時和使用 MFC ODBC 類時,此資訊將適用。

ODBC 管理員將自動安裝 Microsoft 基礎類 (MFC) 庫資料庫支援。 有關 ODBC 管理員計劃的詳細資訊,請參閱[ODBC 管理員](../../data/odbc/odbc-administrator.md)和在線 ODBC API 參考幫助系統。

有關如何為 MFC 資料庫應用程式編寫 ODBC 設定和管理程式的資訊,[技術說明 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。

## <a name="see-also"></a>另請參閱

[ODBC 基礎知識](../../data/odbc/odbc-basics.md)<br/>
[ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)
