---
title: pointers_to_members
ms.date: 11/04/2016
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: 5ee45a77a7094fb1ef9ba536bae391aaad00e812
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180000"
---
# <a name="pointerstomembers"></a>pointers_to_members

**C++特定**

指定類別成員的指標是否可以在其相關類別定義之前宣告，並用來控制解譯指標所需的指標大小和程式碼。

## <a name="syntax"></a>語法

```
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )
```

## <a name="remarks"></a>備註

您可以將放**pointers_to_members**原始程式檔使用替代的 pragma [/vmx](../build/reference/vmb-vmg-representation-method.md)編譯器選項或[繼承關鍵字](../cpp/inheritance-keywords.md)。

*指標宣告*引數會指定是否您已宣告指標成員相關聯的函式定義之前或之後。 *指標宣告*引數可以是下列兩個符號之一：

|引數|註解|
|--------------|--------------|
|*full_generality*|產生安全但有時並非是最佳化的程式碼。 您使用*full_generality*如果相關聯的類別定義之前宣告任何成員的指標。 這個引數一律會使用所指定的指標表示法*大部分一般表示*引數。 等於 /vmg。|
|*best_case*|使用所有成員指標的 best-case 表示，產生安全且最佳化的程式碼。 需要在宣告類別成員的指標之前先定義類別。 預設值是*best_case*。|

*大部分一般表示*引數指定編譯器可以安全地使用參考任何轉譯單位中的類別成員指標的最小指標表示法。 這些引數可以是下列其中一項：

|引數|註解|
|--------------|--------------|
|*single_inheritance*|最常見的表示是單一繼承的成員函式指標。 如果宣告其成員指標類別定義的繼承模型為多重或虛擬，則會產生錯誤。|
|*multiple_inheritance*|最常見的表示是多重繼承的成員函式指標。 如果宣告其成員指標類別定義的繼承模型為虛擬，則會產生錯誤。|
|*virtual_inheritance*|最常見的表示是虛擬繼承的成員函式指標。 永遠不會產生錯誤。 這是預設引數時`#pragma pointers_to_members(full_generality)`用。|

> [!CAUTION]
> 我們建議您把**pointers_to_members** pragma 只能在您想要影響，原始程式碼檔中，只是在任何後`#include`指示詞。 這種作法可使 pragma 影響到其他檔案的風險降低，否則，您會意外地為相同的變數、函式或類別名稱指定多個定義。

## <a name="example"></a>範例

```
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

## <a name="end-c-specific"></a>END C++ 特定的

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)