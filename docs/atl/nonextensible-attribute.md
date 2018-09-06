---
title: nonextensible 屬性 |Microsoft Docs
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
ms.openlocfilehash: 73edae463051aca3ecafac53ae6200df103b8d90
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762137"
---
# <a name="nonextensible-attribute"></a>nonextensible 屬性

如果將不在執行階段擴充的雙重介面 (也就是您將不會提供方法或屬性，透過`IDispatch::Invoke`不是可透過 vtable)，您應該套用**nonextensible**屬性至您的介面定義。 此屬性會提供可用來啟用完整的程式碼在編譯時期的驗證的用戶端語言 （例如 Visual Basic) 的資訊。 如果未提供這個屬性，bug 可能會維持在用戶端程式碼中隱藏執行階段。

如需詳細資訊**nonextensible**屬性和範例，請參閱[nonextensible](../windows/nonextensible.md)。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)

