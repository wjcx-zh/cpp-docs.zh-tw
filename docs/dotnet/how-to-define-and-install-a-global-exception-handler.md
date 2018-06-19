---
title: 如何： 定義與安裝全域例外狀況處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b77e982e3668ca23ece2eeeb5c609d71b30dc908
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129680"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>如何：定義與安裝全域例外狀況處理常式
下列程式碼範例示範如何處理的例外狀況可以擷取。 範例表單包含一個按鈕，按下時，會執行 null 參考，導致系統擲回例外狀況。 這項功能代表一般的程式碼失敗。 Main 函式會安裝應用程式層級例外狀況處理常式會攔截產生的例外狀況。  
  
 這會透過繫結的委派<xref:System.Windows.Forms.Application.ThreadException>事件。 在此情況下，後續的例外狀況會再傳送至`App::OnUnhandled`方法。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)