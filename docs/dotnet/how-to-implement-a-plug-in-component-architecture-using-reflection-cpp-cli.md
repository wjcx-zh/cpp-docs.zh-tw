---
title: "實作外掛程式架構 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- plug-ins [C++]
- reflection [C++}, plug-ins
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 05c6c2584e39ed145a30c919ed850aac45905a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-implement-a-plug-in-component-architecture-using-reflection-ccli"></a>如何：使用反映實作外掛程式元件架構 (C++/CLI)
下列程式碼範例示範如何使用反映來實作簡單的 「 外掛程式 」 架構。 第一個清單是應用程式，而第二個是外掛程式。 應用程式是填入本身的任何表單為基礎的類別做為命令列引數提供的外掛程式 DLL 中找到多個文件格式。  
  
 應用程式嘗試載入使用提供的組件<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>方法。 如果成功，組件內的類型會列舉使用<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>方法。 每個型別即檢查的相容性使用<xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName>方法。 在此範例中，提供的組件中找到的類別必須衍生自<xref:System.Windows.Forms.Form>才能限定為外掛程式類別。  
  
 然後會使用具現化相容類別<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>方法，它接受<xref:System.Type>做為引數和傳回的新執行個體的指標。 然後附加到表單，顯示每個新的執行個體。  
  
 請注意，<xref:System.Reflection.Assembly.Load%2A>方法不會接受包含副檔名的組件名稱。 應用程式中的 main 函式會修剪任何提供的擴充功能，因此下列程式碼範例都可以運作。  
  
## <a name="example"></a>範例  
 下列程式碼會定義應用程式可接受的外掛程式。必須提供組件名稱做為第一個引數。 這個組件應包含至少一個公用<xref:System.Windows.Forms.Form>衍生型別。  
  
```  
// plugin_application.cpp  
// compile with: /clr /c  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
  
ref class PluggableForm : public Form  {  
public:  
   PluggableForm() {}  
   PluggableForm(Assembly^ plugAssembly) {  
      Text = "plug-in example";  
      Size = Drawing::Size(400, 400);  
      IsMdiContainer = true;  
  
      array<Type^>^ types = plugAssembly->GetTypes( );  
      Type^ formType = Form::typeid;  
  
      for (int i = 0 ; i < types->Length ; i++) {  
         if (formType->IsAssignableFrom(types[i])) {  
            // Create an instance given the type description.  
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));  
            if (f) {  
               f->Text = types[i]->ToString();  
               f->MdiParent = this;  
               f->Show();  
            }  
         }  
      }  
   }  
};  
  
int main() {  
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");  
   Application::Run(gcnew PluggableForm(a));  
}  
```  
  
## <a name="example"></a>範例  
 下列程式碼會定義三個類別衍生自<xref:System.Windows.Forms.Form>。 當產生的組件名稱的名稱傳遞在上一個清單中的可執行檔時，這三個類別的每個會探索並具現化，儘管它們是裝載的應用程式在編譯時期未知。  
  
```  
// plugin_assembly.cpp  
// compile with: /clr /LD  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
using namespace System::Drawing;  
  
public ref class BlueForm : public Form {  
public:  
   BlueForm() {  
      BackColor = Color::Blue;  
   }  
};  
  
public ref class CircleForm : public Form {  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);  
   }  
};  
  
public ref class StarburstForm : public Form {  
public:  
   StarburstForm(){  
      BackColor = Color::Black;  
   }  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      Pen^ p = gcnew Pen(Color::Red, 2);  
      Random^ r = gcnew Random( );  
      Int32 w = ClientSize.Width;  
      Int32 h = ClientSize.Height;  
      for (int i=0; i<100; i++) {  
         float x1 = w / 2;  
         float y1 = h / 2;  
         float x2 = r->Next(w);  
         float y2 = r->Next(h);  
         args->Graphics->DrawLine(p, x1, y1, x2, y2);  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [反映 (C++/CLI)](../dotnet/reflection-cpp-cli.md)