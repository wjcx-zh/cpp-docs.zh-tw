---
title: "編譯器警告 (層級 1) C4378 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4378"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4378"
ms.assetid: d08e11ef-891a-4752-9a5e-360e7394acf7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4378
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必須取得函式指標才能執行初始設定式，請考慮 System::ModuleHandle::ResolveMethodHandle  
  
 在 **\/clr** 之下，初始設定式符號會包含函式語彙基元，而不是函式指標。您必須使用 <xref:System.ModuleHandle.ResolveMethodHandle%2A>，將語彙基元轉換成指標。  
  
## 範例  
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
  
## 範例  
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