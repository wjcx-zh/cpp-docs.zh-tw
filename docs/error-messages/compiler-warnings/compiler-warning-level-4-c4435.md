---
title: 編譯器警告 （層級 4） C4435 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72c29bd6d9ffdb4eabb036c61d85a6572cef8fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4435"></a>編譯器警告 (層級 4) C4435
'class1' : /vd2 底下的物件配置將因虛擬基底 'class2' 而變更  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 在預設編譯選項 /vd1，衍生類別沒有指定之虛擬基底的 `vtordisp` 欄位。  如果 /vd2 或 `#pragma vtordisp(2)` 生效，`vtordisp` 欄位會出現，變更物件配置。  如果互動的模組以不同的 `vtordisp` 設定編譯，這會導致二進位碼相容性問題。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4435。  
  
```cpp  
// C4435.cpp  
// compile with: /c /W4  
#pragma warning(default : 4435)  
class A  
{  
public:  
    virtual ~A() {}  
};  
  
class B : public virtual A  // C4435  
{};  
```  
  
## <a name="see-also"></a>另請參閱  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [/vd (停用建構替代)](../../build/reference/vd-disable-construction-displacements.md)