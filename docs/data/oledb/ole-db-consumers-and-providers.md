---
title: OLE DB 消費者和提供者 |Microsoft 文件
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
ms.openlocfilehash: 170f45a3581846dc588abf06aec170d66aa0d545
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111386"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB 消費者和提供者
OLE DB 架構使用模型的消費者和提供者。 取用者可讓資料的要求。 提供者回應這些要求將資料放在以表格式格式，並將其傳回給取用者。 任何呼叫，可讓取用者必須實作提供者中。  
  
 技術上定義，取用者是任何系統或應用程式程式碼 （不一定是 OLE DB 元件），可透過 OLE DB 介面的存取資料。 提供者會實作的介面。 因此，提供者是實作 OLE DB 介面，是爲資料的存取權，並將它公開至其他物件 （也就是取用者） 的任何軟體元件。  
  
 取用者角色，根據 OLE DB 介面; 上呼叫的方法OLE DB 提供者會實作所需的 OLE DB 介面。  
  
 OLE DB 會避免條款用戶端和伺服器，因為這些角色不一定具意義，特別是在多層式架構的情況下。 取用者不能是另一個元件的層上的元件，因為它呼叫用戶端元件可能會造成混淆。 此外，提供者有時像是多資料庫驅動程式比伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)