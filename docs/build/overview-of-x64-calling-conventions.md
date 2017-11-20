---
title: "概觀 x64 呼叫慣例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b1b361bf01e067a1fe76829aa4217e87b107915
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-x64-calling-conventions"></a>x64 呼叫慣例概觀
兩個重要差異 x86 和[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]是 64 位元定址功能，以及一般的 16 個 64 位元暫存器設定一般用途。 展開指定的登錄設定，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]使用[__fastcall](../cpp/fastcall.md)呼叫慣例和 risc 例外狀況處理模型。 `__fastcall`慣例是使用前四個引數和堆疊框架的暫存器傳遞其他引數。  
  
 下列編譯器選項可協助您最佳化您的應用程式[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [/favor （專最佳化為架構）](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>呼叫慣例  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]應用程式二進位介面 (ABI) 預設會使用四個暫存器快速呼叫以呼叫慣例。 呼叫堆疊上配置空間，做為被呼叫端若要儲存這些暫存器的陰影存放區。 函式呼叫的引數以及用於這些引數的暫存器不嚴格的一對一對應。 任何引數不符合 8 個位元組，或不是 1、 2、 4 或 8 個位元組，必須由參考加以傳遞。 不會分散到多個暫存器的單一引數。 將 x87 暫存器堆疊是未使用。 它可能會由被呼叫端，但必須視為 volatile 跨函式呼叫。 所有的浮點作業會完成使用 16 XMM 暫存器。 整數引數會在暫存器 RCX、 RDX、 R8 和 R9 中傳遞。 浮點引數會傳入 XMM0L、 XMM1L、 XMM2L 和 XMM3L。 16 位元組引數會參考所傳遞。 在將詳細說明參數傳遞[參數傳遞](../build/parameter-passing.md)。 除了這些暫存器，RAX、 R10、 R11、 XMM4 和 XMM5 會視為 volatile。 所有其他暫存器是靜態的。 暫存器使用方式中的詳細的記載[註冊使用量](../build/register-usage.md)和[呼叫端/被呼叫端儲存註冊](../build/caller-callee-saved-registers.md)。  
  
 呼叫端會負責配置參數至被呼叫端，空間，而且必須配置足夠的空間來儲存四個暫存器參數，即使被呼叫端不接受許多參數。 這會簡化支援沒有原型 C 語言函式和 vararg C/c + + 函式。 Vararg 或 unprototyped 函式的任何浮點值必須在對應一般用途的暫存器中會重複。 任何超過前四個參數必須儲存在堆疊上，上述的第四個在呼叫之前的陰影存放區。 Vararg 函式詳細資料位於[Varargs](../build/varargs.md)。 沒有原型的函式資訊會詳細說明[沒有原型的函式](../build/unprototyped-functions.md)。  
  
## <a name="alignment"></a>對齊  
 大部分的結構對齊自然對齊。 主要的例外狀況是堆疊指標和`malloc`或`alloca`為了協助效能對齊 16 位元組的記憶體。 16 個位元組以上的對齊必須手動完成，但由於 16 個位元組 XMM 作業的一般對齊大小，這應該適用於大部分的程式碼。 如需有關結構配置與對齊，請參閱[類型和儲存體](../build/types-and-storage.md)。 堆疊配置的相關資訊，請參閱[堆疊使用方式](../build/stack-usage.md)。  
  
## <a name="unwindability"></a>Unwindability  
 分葉函式是函式不會變更任何非靜態暫存器。 非分葉函式可能會變更非暫時性 RSP 比方說，呼叫函式，或為區域變數配置額外的堆疊空間。 為了進行復原靜態暫存器，在處理例外狀況時，非分葉函式都必須以靜態資料，說明如何正確回溯任意指令處函式註解。 這項資料會儲存為*pdata*，或程序資料，接著是指*xdata*、 例外狀況處理的資料。 Xdata 包含回溯的資訊，並可以指向其他 pdata 或例外狀況處理常式函式。 初構和終限於高度，讓它們可以正確 xdata 中描述。 堆疊指標必須對齊 16 位元組的程式碼除外的一部分終解或初構不在分葉函式內的任何區域中。 分葉函式可以只是藉由模擬傳回，因此不需要 pdata 和 xdata 進行回溯。 如需函式初構和終適當的結構的詳細資訊，請參閱[初構和終解](../build/prolog-and-epilog.md)。 如需例外狀況處理和例外狀況處理和 pdata 和 xdata 的回溯的詳細資訊，請參閱[例外狀況處理 (x64)](../build/exception-handling-x64.md)。  
  
## <a name="see-also"></a>另請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)