---
title: 轉換提供者不支援的資料
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e60f6cd4f7dca1ed3e176cabefc42f69946436a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033835"
---
# <a name="converting-data-not-supported-by-the-provider"></a>轉換提供者不支援的資料

當取用者要求提供者不支援的資料類型時，OLE DB 提供者範本程式碼`IRowsetImpl::GetData`呼叫 Msdadc.dll 来轉換的資料類型。

如果您實作的介面，例如`IRowsetChange`需要資料轉換，您可以呼叫 Msdaenum.dll 來執行轉換。 使用`GetData`，為 Atldb.h，做為範例中所定義。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)