---
title: 如何：定義與安裝全域例外狀況處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 9c6f355bc43fc53d2b8d27a1ee69c059d0f50692
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534533"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>如何：定義與安裝全域例外狀況處理常式

下列程式碼範例示範如何處理的例外狀況可以擷取。 範例表單包含一個按鈕，按下時，會執行為 null 的參考，導致系統擲回例外狀況。 這項功能代表典型程式碼失敗。 Main 函式會安裝整個應用程式的例外狀況處理常式會攔截產生的例外狀況。

這可以藉由繫結的委派<xref:System.Windows.Forms.Application.ThreadException>事件。 在此情況下，後續的例外狀況則會傳送至`App::OnUnhandled`方法。

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