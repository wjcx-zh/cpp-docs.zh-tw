---
title: 轉換提供者不支援的資料
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e87aebc4d6f23343af9a2f966d2c522e95b304ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211493"
---
# <a name="converting-data-not-supported-by-the-provider"></a>轉換提供者不支援的資料

當取用者要求提供者不支援的資料類型時，`IRowsetImpl::GetData` 的 OLE DB 提供者範本程式碼會呼叫 Msdadc 來轉換資料類型。

如果您執行的介面如需要資料轉換的 `IRowsetChange`，您可以呼叫 Msdaenum 來進行轉換。 使用為 atldb.h 中定義的 `GetData`做為範例。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
