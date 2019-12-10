---
title: 如何：定義與安裝全域例外狀況處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 27666702a548c0c71b7e25597a1927520968b124
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988308"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>如何：定義與安裝全域例外狀況處理常式

下列程式碼範例會示範如何捕捉未處理的例外狀況。 範例表單包含一個按鈕，當按下時，會執行 null 參考，導致擲回例外狀況。 這種功能代表一般的程式碼失敗。 主要函式所安裝的整個應用程式例外狀況處理常式會攔截產生的例外狀況。

這是藉由將委派系結至 <xref:System.Windows.Forms.Application.ThreadException> 事件來完成。 在此情況下，後續的例外狀況就會傳送至 `App::OnUnhandled` 方法。

## <a name="example"></a>範例

```cpp
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

## <a name="see-also"></a>請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)
