---
title: 參考計數 (ATL) |Microsoft 文件
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
ms.openlocfilehash: d1ba27f00bf25f88575101b1299daf50f94000ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358244"
---
# <a name="reference-counting"></a>參考計數
COM 本身不會自動嘗試從記憶體移除物件，其認定不再使用物件時。 相反地，物件的程式設計人員必須移除未使用的物件。 程式設計人員決定是否可以移除物件根據參考計數。  
  
 COM 使用**IUnknown**方法[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)和[發行](http://msdn.microsoft.com/library/windows/desktop/ms682317)，若要管理之介面的物件上的參考計數。 會呼叫這些方法的一般規則：  
  
-   每當用戶端接收的介面指標，`AddRef`必須在介面上呼叫。  
  
-   每當用戶端已完成時使用的介面指標，它必須呼叫**發行**。  
  
 在簡單的實作中，每個`AddRef`增量和每個呼叫**發行**呼叫遞減物件內的計數器變數。 當計數會傳回零時，介面不再有任何使用者，而且可以自由地從記憶體中移除本身。  
  
 參考計數也可以實作，讓每個參考的物件 （不以個別的介面） 會計算。 在此情況下，每個`AddRef`和**發行**物件上呼叫的中央實作的委派和**發行**時參考計數到達零時，將整個物件會釋出。  
  
> [!NOTE]
>  當`CComObject`-衍生的物件建構使用**新**運算子，參考計數為 0。 因此，呼叫`AddRef`必須成功建立後進行`CComObject`-衍生物件。  
  
## <a name="see-also"></a>另請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [管理透過參考計數的物件存留期](http://msdn.microsoft.com/library/windows/desktop/ms687260)

