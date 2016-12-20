---
title: "如何：實作鎖定 C# 關鍵字 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock C# 關鍵字 [C++]"
  - "lock 陳述式"
ms.assetid: 436fe544-ffb7-49b9-9798-90794e9974de
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：實作鎖定 C# 關鍵字 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明如何在 Visual C\+\+ 中實作 C\# `lock` 關鍵字。  如需詳細資訊，請參閱[lock 陳述式](../Topic/lock%20Statement%20\(C%23%20Reference\).md)。  
  
 您也可以使用 C\+\+ 支援程式庫中的 `lock` 類別。  如需詳細資訊，請參閱[同步處理 \(lock 類別\)](../dotnet/synchronization-lock-class.md)。  
  
## 範例  
  
```  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## 請參閱  
 [與其他 .NET 程式設計語言間的互通性](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)