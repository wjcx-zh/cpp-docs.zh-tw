---
title: 設計集合和列舉程式介面 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab8b42804ca892c80971928b869e09ccdf479d68
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851323"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>集合和列舉程式介面的設計原則
有不同的設計原則，每一種介面背後：  
  
-   集合介面會提供*隨機*存取權*單一*透過集合中的項目`Item`方法，它可讓用戶端探索透過集合中有多少項目`Count`屬性，並通常可讓用戶端加入和移除項目。  
  
-   列舉值介面會提供*序列*存取權*多重*集合中的項目，它並不允許用戶端能夠探索 （直到過了列舉值可讓您停止傳回集合中有多少項目項目），而它也未提供任何方式加入或移除項目。  
  
 每一種介面扮演不同的角色提供存取集合中的項目。  
  
## <a name="see-also"></a>另請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)

