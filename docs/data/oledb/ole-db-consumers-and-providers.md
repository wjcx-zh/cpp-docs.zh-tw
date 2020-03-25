---
title: OLE DB 消費者和提供者
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: d57ded9d084971c3562fc7f22e6a1a12a4e3368d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210070"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB 消費者和提供者

OLE DB 架構會使用取用者和提供者的模型。 取用者會要求資料。 提供者會以表格格式放入資料，並將其傳回給取用者，以回應這些要求。 取用者可以進行的任何呼叫都必須在提供者中執行。

就技術上而言，取用者是指透過 OLE DB 介面來存取資料的任何系統或應用程式代碼（不一定是 OLE DB 元件）。 介面會實作為提供者。 因此，提供者就是任何軟體元件，它會執行 OLE DB 介面來封裝對資料的存取，並將其公開給其他物件（也就是取用者）。

針對角色，取用者會在 OLE DB 介面上呼叫方法;OLE DB 提供者會執行所需的 OLE DB 介面。

OLE DB 避免使用用戶端和伺服器這類詞彙，因為這些角色並不一定合理，特別是在多層式的情況下。 因為取用者可以是服務另一個元件之階層上的元件，所以呼叫它時，用戶端元件會造成混淆。 此外，提供者的運作方式有時會比伺服器更像資料庫驅動程式。

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)
