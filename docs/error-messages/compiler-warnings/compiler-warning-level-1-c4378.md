---
title: 編譯器警告 （層級 1） C4378 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4378
dev_langs:
- C++
helpviewer_keywords:
- C4378
ms.assetid: d08e11ef-891a-4752-9a5e-360e7394acf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92f7fa0c455332c443d2651a377d870f12e59522
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4378"></a>編譯器警告 (層級 1) C4378
必須取得函式指標才能執行初始設定式;請考慮 System::ModuleHandle::ResolveMethodHandle  
  
 在下 **/clr**，初始設定式符號包含函式語彙基元，而不是函式指標。  您需要將語彙基元轉換成指標使用<xref:System.ModuleHandle.ResolveMethodHandle%2A>。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4378。  
  
```  
// C4378.cpp  
// compile with: /W1 /clr /c  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors to call  
PF pfx[200];   // ptrs to those dtors, watch for overflow  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() {}  
   ~A() {}  
};  
  
A aaaa;   
  
#pragma data_seg(".mine$a")  
PF InitSegStart = (PF)1;  
#pragma data_seg(".mine$z")  
PF InitSegEnd = (PF)1;  
#pragma data_seg()  
  
void InitializeObjects () {  
   PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if (*x)  
         (*x)();  
}  
  
#pragma init_seg(".mine$m",myexit)   // C4378  
A bbbb;   // crash  
  
int main () {  
   InitializeObjects();  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何解決 C4378。  
  
```  
// C4378_b.cpp  
// compile with: /clr  
#pragma warning(disable:4378)  
using namespace System;  
typedef void (__cdecl *PF)(void);  
typedef void (__clrcall * CLRPF)(void);  
  
int cxpf = 0;  // number of destructors we need to call  
PF pfx[200];   // ptrs to those dtors. Watch out for overflow!  
  
ref class TypeClassHolder {  
public:  
   static TypeClassHolder ^typeClass = gcnew TypeClassHolder();  
};  
  
CLRPF FuncTokenToFuncPtr(PF tknFunc) {  
   ModuleHandle type =   
      Type::GetTypeFromHandle(Type::GetTypeHandle(TypeClassHolder::typeClass))->Module->ModuleHandle;  
   return (CLRPF)type.ResolveMethodHandle((int)(size_t)(tknFunc)).GetFunctionPointer().ToPointer();  
}  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() {}  
   ~A() {}  
};  
  
A aaaa;   
  
#pragma data_seg(".mine$a")  
PF InitSegStart = (PF)1;  
#pragma data_seg(".mine$z")  
PF InitSegEnd = (PF)1;  
#pragma data_seg()  
  
void InitializeObjects () {  
   PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if(*x) {  
         CLRPF realppfunc;  
         realppfunc = FuncTokenToFuncPtr(*x);  
         (realppfunc)();  
      }  
}  
  
#pragma init_seg(".mine$m",myexit)  
A bbbb; // constructor call succeeds  
  
int main () {  
   InitializeObjects();  
}  
```