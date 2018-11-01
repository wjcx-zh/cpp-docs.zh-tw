---
title: 增強簡單唯讀提供者
ms.date: 10/26/2018
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
ms.openlocfilehash: 4b06eb77851df0bf0bd0d3ef91a3ea960835ccba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462916"
---
# <a name="enhancing-the-simple-read-only-provider"></a>增強簡單唯讀提供者

本節說明如何增強[簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)在上一節中建立。 `IRowsetLocateImpl` 建立實作`IRowsetLocate`介面，並加入您的書籤支援。

當您有運作的提供者時，您可以增強程式碼進行更新提供者、 處理交易，或強化的資料列擷取的演算法效能。 大部分的提供者增強功能包括將介面加入至現有的 COM 物件。

下列主題中的範例藉由新增增強的資料列擷取機制`IRowsetLocate`介面`CAgentRowset`。 本主題說明如何以：

- [請繼承自 IRowsetLocate RCustomRowset](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)。

- [動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。

## <a name="see-also"></a>另請參閱

[建立簡單唯讀提供者](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
