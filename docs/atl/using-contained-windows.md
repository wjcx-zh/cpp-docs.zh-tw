---
title: 使用包含的 Windows |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c3b439baf05c4e4287613e9b6b5a9b1c2546b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357917"
---
# <a name="using-contained-windows"></a>使用包含的 Windows
ATL 實作包含的 windows [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)。 包含的視窗表示可委派給容器物件，而不是在它自己的類別中處理這些訊息的視窗。  
  
> [!NOTE]
>  您不需要自`CContainedWindowT`才能使用所包含的 windows。  
  
 包含視窗，您可以是超級類別，現有的 Windows 類別或子類別化現有的視窗。 若要建立該超級類別現有的 Windows 視窗類別中，先將現有的類別名稱指定的建構函式`CContainedWindowT`物件。 然後呼叫`CContainedWindowT::Create`。 子類別化現有的視窗，您不需要指定 Windows 類別名稱 (傳遞**NULL**建構函式)。 只需呼叫`CContainedWindowT::SubclassWindow`方法正在子類別化視窗的控制代碼。  
  
 通常，您會使用包含的 windows 做為資料成員的容器類別。 容器不需要是視窗;不過，它必須衍生自[CMessageMap](../atl/reference/cmessagemap-class.md)。  
  
 包含的視窗可以使用替代的訊息對應來處理它的訊息。 如果您有一個以上的包含的視窗時，您應該宣告多個替代訊息對應，各有一個對應至個別的包含視窗。  
  
## <a name="example"></a>範例  
 以下是具有兩個包含視窗的容器類別的範例：  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 如需有關包含 windows 的詳細資訊，請參閱[SUBEDIT](../visual-cpp-samples.md)範例。  
  
## <a name="see-also"></a>另請參閱  
 [視窗類別](../atl/atl-window-classes.md)

