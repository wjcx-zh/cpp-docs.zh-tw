---
title: "new (new slot in vtable)  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "new keyword [C++]"
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# new (new slot in vtable)  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`new` 關鍵字表示虛擬成員會取得 vtable 的新位置。  
  
> [!NOTE]
>  `new` 關鍵字有許多用途和意義。  如需詳細資訊，請參閱[new](../misc/new.md)主題中的＜澄清＞。  
  
## 所有執行階段  
 \(這個語言功能沒有適用於所有執行階段的備註\)。  
  
## Windows 執行階段  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]不支援此項  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 在 **\/clr** 編輯， `new` 表示虛擬成員會取得 vtable 的新位置；函式不會覆寫基底類別方法。  
  
 `new` 會導致 newslot 修飾詞加入至函式的 IL。如需 newslot 的詳細資訊，請參閱 。  
  
-   [\<caps:sentence id\="tgt11" sentenceid\="e9bb59a12f97840a5c3173bb77c6b5b1" class\="tgtSentence"\>MethodInfo.GetBaseDefinition 方法\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [\<caps:sentence id\="tgt12" sentenceid\="f6ceddd85a425f38e7ed06e94a9808a9" class\="tgtSentence"\>MethodAttributes 列舉\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列範例示範 `new` 的效用。  
  
```  
// newslot.cpp  
// compile with: /clr  
ref class C {  
public:  
   virtual void f() {  
      System::Console::WriteLine("C::f() called");  
   }  
  
   virtual void g() {  
      System::Console::WriteLine("C::g() called");  
   }  
};  
  
ref class D : public C {  
public:  
   virtual void f() new {  
      System::Console::WriteLine("D::f() called");  
   }  
  
   virtual void g() override {  
      System::Console::WriteLine("D::g() called");  
   }  
};  
  
ref class E : public D {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("E::f() called");  
   }  
};  
  
int main() {  
   D^ d = gcnew D;  
   C^ c = gcnew D;  
  
   c->f();   // calls C::f  
   d->f();   // calls D::f  
  
   c->g();   // calls D::g  
   d->g();   // calls D::g  
  
   D ^ e = gcnew E;  
   e->f();   // calls E::f  
}  
```  
  
 **Output**  
  
  **C::f\(\) called**  
 **D::f\(\) called**  
 **D::g\(\) called**  
 **D::g\(\) called**  
 **E::f\(\) called**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)   
 [覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)