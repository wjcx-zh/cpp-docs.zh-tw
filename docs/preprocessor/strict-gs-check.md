---
title: strict_gs_check |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs:
- C++
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b58b02781f266b24fa321b3849f42b2e090b860
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842972"
---
# <a name="strictgscheck"></a>strict_gs_check
這個 pragma 提供增強的安全性檢查。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## <a name="remarks"></a>備註  
 指示編譯器在函式堆疊中隨機插入 Cookie，協助偵測部分堆疊型緩衝區滿溢分類。 根據預設，/GS (緩衝區安全性檢查) 編譯器選項不會插入所有函式皆適用的 Cookie。 如需詳細資訊，請參閱 [/GS (緩衝區安全性檢查)](../build/reference/gs-buffer-security-check.md)。  
  
 您必須以 /GS (緩衝區安全性檢查) 編譯，才能啟用 strict_gs_check。  
  
 請在可能接觸到有害資料的程式碼模組中使用這個 pragma。 這個 pragma 非常主動，且可套用至可能不需要這個防禦機制的函式，不過這個 pragma 經過最佳化後，可將對所產生應用程式的效能的影響降至最低。  
  
 即使您使用這個 pragma，仍應盡可能撰寫安全的程式碼。 也就是說，請確定您的程式碼已無緩衝區滿溢。 strict_gs_check 可能從不要保留在您的程式碼的緩衝區滿溢保護您的應用程式。  
  
## <a name="example"></a>範例  
 在下列程式碼中，當我們將陣列複製到本機陣列時，即發生緩衝區滿溢。 當您使用 /GS 編譯此程式碼時，不會在堆疊中插入任何 Cookie，因為陣列資料類型是指標。 新增 strict_gs_check pragma 會強制堆疊 Cookie 插入函式堆疊。  
  
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
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/GS (緩衝區安全性檢查)](../build/reference/gs-buffer-security-check.md)