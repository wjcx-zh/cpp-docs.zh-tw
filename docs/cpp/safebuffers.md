---
title: "safebuffers |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb9541bfc4a94253ac26e118e22c3abb2663a893
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="safebuffers"></a>safebuffers
**Microsoft 特定的**  
  
 告知編譯器不要插入函式的緩衝區滿溢安全性檢查。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>備註  
 **/GS**編譯器選項可讓編譯器在堆疊上插入安全性檢查來測試緩衝區滿溢。 進行安全性檢查的資料結構的類型描述[/GS （緩衝區安全性檢查）](../build/reference/gs-buffer-security-check.md)。 如需緩衝區滿溢偵測的詳細資訊，請參閱[編譯器安全性檢查在深度](http://go.microsoft.com/fwlink/p/?linkid=7260)MSDN 網站上。  
  
 某位專業人員手動檢閱程式碼或進行外部分析後，可能會判斷函式不會發生緩衝區滿溢。 在此情況下，您可以隱藏函式的安全性檢查，藉由套用`__declspec(safebuffers)`函式宣告的關鍵字。  
  
> [!CAUTION]
>  緩衝區安全性檢查提供了重要的安全性保護，且幾乎不會對效能造成影響。 因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。  
  
## <a name="inline-functions"></a>內嵌函式  
 A*主要函式*可以使用[內嵌](inline-functions-cpp.md)關鍵字來插入一份*次要函式*。 如果`__declspec(safebuffers)`關鍵字套用至函式時，緩衝區滿溢偵測會抑製該函式。 不過，內嵌會影響`__declspec(safebuffers)`如下的關鍵字。  
  
 假設**/GS**編譯器選項已指定這兩個函式，但主要功能指定`__declspec(safebuffers)`關鍵字。 第二個函式中的資料結構會使其進行安全性檢查，因此函式不會抑制這些檢查。 在此情況下：  
  
-   指定[__forceinline](inline-functions-cpp.md)關鍵字次要函式，以強制編譯器內嵌該函式，不論編譯器最佳化。  
  
-   第二個函式會進行安全性檢查，因為安全性檢查也會套用至主要函式即使它會指定`__declspec(safebuffers)`關鍵字。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`__declspec(safebuffers)`關鍵字。  
  
```  
// compile with: /c /GS  
typedef struct {  
    int x[20];  
} BUFFER;  
static int checkBuffers() {  
    BUFFER cb;  
    // Use the buffer...  
    return 0;  
};  
static __declspec(safebuffers)   
    int noCheckBuffers() {  
    BUFFER ncb;  
    // Use the buffer...  
    return 0;  
}  
int wmain() {  
    checkBuffers();  
    noCheckBuffers();  
    return 0;  
}  
```  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [inline、 __inline、 \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)