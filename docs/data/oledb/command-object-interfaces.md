---
title: 命令物件介面
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 755c44cf8d0cb5bf5066197bfd0ead3e0f25e1f9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032397"
---
# <a name="command-object-interfaces"></a>命令物件介面

命令物件會使用`IAccessor`介面來指定參數繫結。 取用者可以呼叫`IAccessor::CreateAccessor`，它會將陣列傳遞`DBBINDING`結構。 `DBBINDING` 包含資料行繫結 （例如型別和長度） 的相關資訊。 提供者會收到結構，並判斷應該傳送資料的方式，以及是否需要轉換。

`ICommandText`介面可用來指定文字的命令。 `ICommandProperties`介面處理命令的所有屬性。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
