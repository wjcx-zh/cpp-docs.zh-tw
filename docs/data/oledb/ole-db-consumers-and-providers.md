---
title: OLE DB 消費者和提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b37a06ec89f0e2e21c4332a480e58c605f0d161f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110714"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB 消費者和提供者

OLE DB 架構會使用取用者和提供者模型。 取用者提出資料要求。 提供者會將資料放在表格式的格式，並將它傳回給取用者回應這些要求。 在提供者必須實作任何取用者可以進行的呼叫。  
  
技術上的定義，取用者是任何系統或應用程式程式碼 （不一定是 OLE DB 元件），可透過 OLE DB 介面存取資料。 在提供者會實作的介面。 因此，提供者是實作封裝資料的存取權，並將它公開給其他物件 （也就是消費者） 的 OLE DB 介面的任何軟體元件。  
  
根據角色，取用者，請呼叫 OLE DB 介面; 上的方法OLE DB 提供者會實作所需的 OLE DB 介面。  
  
因為這些角色不一律具意義，尤其是在多層式架構的情況下，OLE DB 會避免條款用戶端和伺服器。 因為取用者可能是另一個元件的層上的元件，呼叫這個方法的用戶端元件會造成混淆。 此外，提供者有時更像是伺服器以外的資料庫驅動程式。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)