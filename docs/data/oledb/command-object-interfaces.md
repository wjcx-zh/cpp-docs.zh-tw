---
title: 命令物件介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8176bad2921edd22edaab1688e38bc7de275b0bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074796"
---
# <a name="command-object-interfaces"></a>命令物件介面

命令物件會使用`IAccessor`介面來指定參數繫結。 取用者可以呼叫`IAccessor::CreateAccessor`，它會將陣列傳遞`DBBINDING`結構。 `DBBINDING` 包含資料行繫結 （例如型別和長度） 的相關資訊。 提供者會收到結構，並判斷應該傳送資料的方式，以及是否需要轉換。

`ICommandText`介面可用來指定文字的命令。 `ICommandProperties`介面處理命令的所有屬性。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)