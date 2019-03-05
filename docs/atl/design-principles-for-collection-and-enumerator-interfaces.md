---
title: 設計集合和列舉程式介面 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: f40c86d3bc8d9b4e4c752fe6657f6a5a14f19e0c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269926"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>集合和列舉程式介面的設計原則

有不同的設計原則，每一種介面背後：

- 集合介面會提供*隨機*存取權*單一*透過集合中的項目`Item`方法，它可讓用戶端探索透過集合中有多少項目`Count`屬性，並通常可讓用戶端加入和移除項目。

- 列舉值介面會提供*序列*存取權*多重*集合中的項目，它並不允許用戶端能夠探索 （直到過了列舉值可讓您停止傳回集合中有多少項目項目），而它也未提供任何方式加入或移除項目。

每一種介面扮演不同的角色提供存取集合中的項目。

## <a name="see-also"></a>另請參閱

[集合和列舉程式](../atl/atl-collections-and-enumerators.md)
