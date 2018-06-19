---
title: vtordisp |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 502425728fcd97d2ae8d2efe406dc73370de1272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841768"
---
# <a name="vtordisp"></a>vtordisp
**C + + 特定的**  
  
 加入隱藏 vtordisp 建構函式/解構函式替代成員的控制項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#pragma vtordisp([push,] n)  
#pragma vtordisp(pop)  
#pragma vtordisp()  
#pragma vtordisp([push,] {on | off})  
```  
  
#### <a name="parameters"></a>參數  
 `push`  
 在內部編譯器堆疊上推入目前的 vtordisp 設定，並將新的 vtordisp 設定設為 `n`。  如果未指定 `n`，則不會變更目前的 vtordisp 設定。  
  
 `pop`  
 從內部編譯器堆疊中移除最上方的記錄，並將 vtordisp 設定還原為已移除的值。  
  
 `n`  
 為 vtordisp 設定指定新的值。 可能的值為 0、1 或 2，對應到 /vd0、/vd1 和 /vd2 編譯器選項。 如需詳細資訊，請參閱[/vd （停用建構替代）](../build/reference/vd-disable-construction-displacements.md)。  
  
 `on`  
 相當於 `#pragma vtordisp(1)`。  
  
 `off`  
 相當於 `#pragma vtordisp(0)`。  
  
## <a name="remarks"></a>備註  
 `vtordisp` pragma 只適用於使用虛擬基底的程式碼。 如果衍生類別會覆寫它從虛擬基底類別繼承的虛擬函式，而且如果衍生類別的建構函式或解構函式會使用虛擬基底類別的指標呼叫函式，編譯器可能會在內含虛擬基底的類別中採用額外的隱藏 `vtordisp` 欄位。  
  
 `vtordisp` pragma 會影響其後類別的配置。 /vd0、/vd1 和 /vd2 選項指定了與完整模組相同的行為。 指定 `0` 或 `off` 會抑制隱藏的 `vtordisp` 成員。 只有在類別的建構函式和解構函式無法呼叫由 `vtordisp` 指標所指向物件的虛擬函式時，才關閉 `this`。  
  
 指定 `1` 或 `on` 時，預設會在所需的位置啟用隱藏的 `vtordisp` 成員。  
  
 指定`2`啟用隱藏`vtordisp`具有虛擬函式的所有虛擬基底的成員。  `vtordisp(2)` 可能需要確保正確的效能`dynamic_cast`部分建構的物件上。 如需詳細資訊，請參閱[編譯器警告 （層級 1） C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)。  
  
 `#pragma vtordisp()` (不含引數)，將 vtordisp 設定還原為其初始設定值。  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)