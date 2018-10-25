---
title: 將資料提供者不支援轉換 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 79889125675a3e544802eb700718dee0829457c5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066119"
---
# <a name="converting-data-not-supported-by-the-provider"></a>轉換提供者不支援的資料

當取用者要求提供者不支援的資料類型時，OLE DB 提供者範本程式碼`IRowsetImpl::GetData`呼叫 Msdadc.dll 来轉換的資料類型。

如果您實作的介面，例如`IRowsetChange`需要資料轉換，您可以呼叫 Msdaenum.dll 來執行轉換。 使用`GetData`，為 Atldb.h，做為範例中所定義。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)