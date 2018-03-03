---
title: "如何： 宣告固定的指標和實值類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e928fc267bb9e5ec13aeb4f07718454742e60ded
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>如何：宣告固定的指標和實值類型
實值類型可以隱含成為 Boxed。 然後，您可以宣告實值類型物件的 pin 指標本身，並使用**pin_ptr**對 boxed 實值類型。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
8  
7  
7  
```  
  
## <a name="see-also"></a>請參閱  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)