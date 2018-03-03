---
title: "設計集合和列舉程式介面 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8709274e1b95816dee01b4457993521dde5d5213
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>集合和列舉程式介面的設計原則
有不同的設計原則，之後每一種介面：  
  
-   集合介面提供*隨機*存取*單一*透過集合中的項目**項目**方法，它可讓用戶端探索集合中有多少項目透過**計數**屬性，而且通常允許用戶端加入和移除項目。  
  
-   列舉程式介面提供*序列*存取*多個*集合中的項目，它並不允許用戶端探索 （直到列舉值可讓您停止傳回集合中有多少項目項目），以及它並不提供任何方式加入或移除項目。  
  
 每一種介面扮演不同角色中提供存取集合中的項目。  
  
## <a name="see-also"></a>請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)

