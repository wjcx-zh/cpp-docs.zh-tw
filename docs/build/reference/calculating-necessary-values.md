---
title: 計算需要的值
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 75952bbcdf823aa675b35702841c81e511105ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272646"
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
