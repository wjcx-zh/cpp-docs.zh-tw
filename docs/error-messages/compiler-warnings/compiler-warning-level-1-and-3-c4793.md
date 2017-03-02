---
title: "編譯器警告 （層級 1 和 3） C4793 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4793
dev_langs:
- C++
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: a217d2074affa1598aef93882fb299c6fcdef5a6
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-and-3-c4793"></a>編譯器警告 (層級 1 和 3) C4793
'function': 函式會編譯為原生程式碼: 'reason'  
  
 編譯器無法編譯*函式*managed 程式碼，即使[/clr](../../build/reference/clr-common-language-runtime-compilation.md)編譯器選項指定。 相反地，編譯器會發出警告 C4793 和說明的接續訊息，並將編譯*函式*到原生程式碼。 這個接續訊息包含*原因*解釋為什麼的文字*函式*無法編譯成`MSIL`。  
  
 這是層級 1 警告，當您指定`/clr:pure`編譯器選項。  **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 下表列出所有可能的接續訊息。  
  
|原因的訊息|備註|  
|--------------------|-------------|  
|對齊的資料類型不支援在 managed 程式碼|CLR 必須要能夠配置資料，如有需要不可能進行這類的資料對齊與宣告[__m128](../../cpp/m128.md)或[對齊](../../cpp/align-cpp.md)。|  
|Managed 程式碼中不支援使用 '__ImageBase' 的函式|`__ImageBase`是通常用來載入 DLL 只能由低階原生程式碼的連結器特殊符號。|  
|varargs 不支援 ' / clr' 編譯器選項|原生函式無法呼叫 managed 函式具有[變數引數清單](../../cpp/functions-with-variable-argument-lists-cpp.md)varargs 因為這些函式具有不同的堆疊配置需求。 不過，如果您指定`/clr:pure`編譯器選項，因為組件可包含 managed 函式僅支援清單的變數引數。 如需詳細資訊，請參閱[純程式碼及可驗證程式碼 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|  
|64 位元 CLR 不支援以 __ptr32 修飾詞宣告的資料|指標必須在目前平台的原生指標相同的大小。 如需詳細資訊，請參閱[__ptr32、 \__ptr64](../../cpp/ptr32-ptr64.md)。|  
|32 位元 CLR 不支援以 __ptr64 修飾詞宣告的資料|指標必須在目前平台的原生指標相同的大小。 如需詳細資訊，請參閱[__ptr32、 \__ptr64](../../cpp/ptr32-ptr64.md)。|  
|一或多個內建函式不支援在 managed 程式碼|內建函式名稱不就會發出訊息時使用。 不過，內建函式，會導致此訊息通常代表低階的機器指令。|  
|內嵌原生組譯碼 ('__asm') 不支援在 managed 程式碼|[內嵌組譯碼](../../assembler/inline/asm.md)可以包含任意的原生程式碼，無法管理它。|  
|非 __clrcall 虛擬函式，thunk 必須以原生編譯|非[__clrcall](../../cpp/clrcall.md)虛擬函式的 thunk，必須使用未受管理的位址。|  
|使用 '_setjmp' 的函式必須以原生編譯|CLR 必須能夠控制執行程式。 不過， [setjmp](../../cpp/using-setjmp-longjmp.md)函式會執行定期程式略過，請儲存並還原低階資訊，如登錄和執行狀態。|  
  
## <a name="example"></a>範例  
 下列範例會產生 C4793。  
  
```  
// C4793.cpp  
// compile with: /c /clr /W3   
// processor: x86  
int asmfunc(void) {   // C4793, compiled as unmanaged, native code  
   __asm {  
      mov eax, 0  
   }  
}  
```  
  
```Output  
warning C4793: 'asmfunc' : function is compiled as native code:  
        Inline native assembly ('__asm') is not supported in managed code  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C4793。  
  
```  
// C4793_b.cpp  
// compile with: /c /clr /W3  
#include <setjmp.h>  
jmp_buf test_buf;  
  
void f() {  
   setjmp(test_buf);   // C4793 warning  
}  
```  
  
```Output  
warning C4793: 'f' : function is compiled as native code:  
        A function using '_setjmp' must be compiled as native  
```
