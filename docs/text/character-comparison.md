---
title: 字元比較
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 075a22634f254c2ea634a1171ee157971fe5918e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749330"
---
# <a name="character-comparison"></a>字元比較

使用下列秘訣：

- 比較以 ASCII 字元一個已知的前導位元組正常運作：

    ```cpp
    if( *sz1 == 'A' )
    ```

- 比較兩個未知的字元需要使用其中一種 Mbstring.h> 中定義的巨集：

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   這可確保會比較是否相等的雙位元組字元的兩個位元組。

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)<br/>
[緩衝區溢位](../text/buffer-overflow.md)
