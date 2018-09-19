---
title: 參考計數 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9288eda15b0bac3d3694ee56a2f427aefb60e032
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086430"
---
# <a name="reference-counting"></a>參考計數

COM 本身不會自動嘗試將物件從記憶體移除它認為不再使用物件時。 相反地，物件程式設計人員必須移除未使用的物件。 程式設計人員決定是否可以移除物件根據參考計數。

COM 使用`IUnknown`方法， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)並[發行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)來管理物件上的介面的參考計數。 呼叫這些方法的一般規則是：

- 每當用戶端接收的介面指標，`AddRef`必須呼叫的介面上。

- 每當用戶端完成使用的介面指標時，必須呼叫`Release`。

在簡單的實作中，每個`AddRef`增量和每個呼叫`Release`呼叫遞減物件內的計數器變數。 當計數會傳回零時，介面不會再有任何使用者，而且可以自由地從記憶體中移除本身。

參考計數也可以實作，讓每個參考的物件 （不是以個別的介面） 會計算。 在此情況下，每個`AddRef`並`Release`物件上呼叫集中實作的委派和`Release`時參考計數到達零時，會釋出整個物件。

> [!NOTE]
>  當`CComObject`-衍生的物件使用建構**新**運算子的參考計數為 0。 因此，呼叫`AddRef`必須設定為已成功建立之後`CComObject`-衍生物件。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[管理透過參考計數的物件存留期](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)

