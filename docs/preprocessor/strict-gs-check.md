---
title: strict_gs_check pragma
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 0b66e87f2280c923d05103fccfcbbc8d32daf3fd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216591"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check pragma

這個 pragma 提供增強的安全性檢查。

## <a name="syntax"></a>語法

> **#pragma strict_gs_check (** [ **push,** ] { **on**  |  **off** } **)** \
> **#pragma strict_gs_check (pop)**

## <a name="remarks"></a>備註

指示編譯器在函式堆疊中隨機插入 Cookie，協助偵測部分堆疊型緩衝區滿溢分類。 根據預設, `/GS` (緩衝區安全性檢查) 編譯器選項不會針對所有函式插入 cookie。 如需詳細資訊，請參閱 [/GS (緩衝區安全性檢查)](../build/reference/gs-buffer-security-check.md)。

使用`/GS`進行編譯以啟用**strict_gs_check**。

請在可能接觸到有害資料的程式碼模組中使用這個 pragma。 **strict_gs_check**是積極的 pragma, 適用于可能不需要這項防禦的函式, 但已進行優化, 以將其對產生的應用程式效能的影響降至最低。

即使您使用這個 pragma，仍應盡可能撰寫安全的程式碼。 也就是, 請確定您的程式碼沒有緩衝區溢位。 **strict_gs_check**可保護您的應用程式免于緩衝區溢位, 而不會保留在您的程式碼中。

## <a name="example"></a>範例

在此範例中, 當我們將陣列複製到本機陣列時, 就會發生緩衝區溢位。 當您使用`/GS`編譯此程式碼時, 不會在堆疊中插入任何 cookie, 因為陣列資料類型是指標。 新增**strict_gs_check** pragma 會強制堆疊 cookie 進入函式堆疊。

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // *** This buffer is subject to being overrun!! ***
    void *pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS (緩衝區安全性檢查)](../build/reference/gs-buffer-security-check.md)
