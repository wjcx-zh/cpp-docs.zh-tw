---
title: 衝突與 x86 編譯器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f01e65adfb42a5fb3361e75ce34060f7dc1b9f9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709666"
---
# <a name="conflicts-with-the-x86-compiler"></a>與 x86 編譯器衝突

資料類型都大於 4 個位元組會不會自動對齊堆疊上時使用 x86 編譯器來編譯應用程式。 因為 x86 編譯器是 4 位元組對齊的堆疊，任何大於 4 個位元組，比方說，64 位元整數，不會自動對齊 8 位元組位址的架構。

處理未對齊的資料有兩個含意。

- 可能需要較長的時間比所需存取對齊的位置存取未對齊的位置。

- 未對齊的位置不能在連鎖的作業。

如果您需要更多嚴格的對齊方式，使用`__declspec(align(N)) on your variable declarations`。 這可讓編譯器動態地對齊的堆疊，以符合您的規格。 不過，動態調整堆疊，在執行階段可能會導致您的應用程式的執行速度緩慢。

## <a name="see-also"></a>另請參閱

[類型和儲存區](../build/types-and-storage.md)<br/>
[align](../cpp/align-cpp.md)