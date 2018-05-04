---
title: nonextensible 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40b4b79701862ca07e704aca098419479923ef1a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="nonextensible-attribute"></a>nonextensible 屬性
如果將不在執行階段擴充雙重介面 (也就是您將不會提供方法或屬性，透過**idispatch:: Invoke**不提供透過 vtable)，您應該套用**nonextensible**介面定義的屬性。 此屬性會提供可用來啟用完整的程式碼驗證，在編譯時期的用戶端語言 （例如 Visual Basic) 的資訊。 如果未提供這個屬性，bug 可能會隱藏在用戶端程式碼直到執行階段。  
  
 如需有關**nonextensible**屬性和範例，請參閱[nonextensible](../windows/nonextensible.md)。  
  
## <a name="see-also"></a>另請參閱  
 [雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)

