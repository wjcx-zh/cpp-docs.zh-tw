---
title: 計算需要的值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e56acaecd038b7580423e078459e39994391052a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722354"
---
# <a name="calculating-necessary-values"></a>計算需要的值

計算延遲 helper 常式需要兩項關鍵的資訊。 因此，兩個內嵌函式中有 delayhlp.cpp 計算這項資訊。

- 第一個計算目前的匯入 （匯入位址表 (IAT)、 繫結的匯入位址表格 (BIAT)，以及未繫結的匯入位址表格 (UIAT)） 的三個不同資料表的索引。

- 第二個計算中有效的 IAT 的匯入的數目。

```cpp
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="see-also"></a>另請參閱

[了解協助協助程式函式](understanding-the-helper-function.md)