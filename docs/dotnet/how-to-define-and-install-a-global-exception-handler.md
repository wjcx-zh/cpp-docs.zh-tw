---
title: "如何：定義與安裝全域例外狀況處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "處理常式, 全域"
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：定義與安裝全域例外狀況處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例示範未處理的例外狀況如何擷取。  範例表單包含，，當按下，執行 null 參考的按鈕，導致擲回例外狀況。  這項功能表示一般程式碼失敗。  發生的例外狀況是由主函式安裝的應用程式例外處理常式攔截。  
  
 這是透過繫結 <xref:System.Windows.Forms.Application.ThreadException> 事件的委派。  在這種情況下，後續例外狀況就會傳送至 `App::OnUnhandled` 方法。  
  
## 範例  
  
```  
// global_exception_handler.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Drawing;  
using namespace System::Windows::Forms;  
  
ref class MyForm : public Form  
{  
   Button^ b;  
public:  
   MyForm( )  
   {  
      b = gcnew Button( );  
      b->Text = "Do Null Access";  
      b->Size = Drawing::Size(150, 30);  
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);  
      Controls->Add(b);  
   }  
   void OnClick(Object^ sender, EventArgs^ args)   
   {  
      // do something illegal, like call through a null pointer...  
      Object^ o = nullptr;  
      o->ToString( );        
   }  
};  
  
ref class App  
{  
public:  
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)  
   {  
      MessageBox::Show(e->Exception->Message, "Global Exeception");  
      Application::ExitThread( );  
   }  
};  
  
int main()  
{  
   Application::ThreadException += gcnew   
      ThreadExceptionEventHandler(App::OnUnhandled);  
  
   MyForm^ form = gcnew MyForm( );  
   Application::Run(form);  
}  
```  
  
## 請參閱  
 [Exception Handling](../windows/exception-handling-cpp-component-extensions.md)