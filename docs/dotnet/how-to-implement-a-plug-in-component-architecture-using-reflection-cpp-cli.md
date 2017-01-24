---
title: "如何：使用反映實作外掛程式元件架構 (C++/CLI) | Microsoft Docs"
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
  - "外掛程式 [C++]"
  - "反映 [C++], 外掛程式"
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用反映實作外掛程式元件架構 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範使用反映以實作簡單的「外掛程式」架構。  第一個列表是應用程式，第二個是外掛程式。  應用程式是多重文件表單，會使用任何在外掛程式 DLL \(以命令列引數的方式提供\) 中找到的表單架構類別，將資料填入表單。  
  
 應用程式會使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法，嘗試載入提供的組件。  如果成功，則會使用 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> 方法列舉組件中的型別。  接著使用 <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> 方法檢查每個型別的相容性。  在這個範例中，在提供的組件中找到的類別必須衍生自 <xref:System.Windows.Forms.Form> 類別，才會視為外掛程式。  
  
 接著相容的類別會以 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 方法執行個體化，此方法可接受 <xref:System.Type> 做為引數並會傳回新執行個體的指標。  每個新的執行個體會附加至表單並顯示在表單中。  
  
 請注意 <xref:System.Reflection.Assembly.Load%2A> 方法不接受含有副檔名的組件名稱。  因為應用程式的主函式會修剪掉任何提供的副檔名，所以不管組件名稱有無副檔名，下列程式碼範例都可以運作。  
  
## 範例  
 下列程式碼定義接受外掛程式的應用程式。  必須提供組件名稱做為第一個引數。  這個組件應該包含至少一個公用的 <xref:System.Windows.Forms.Form> 衍生型別。  
  
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
  
## 範例  
 下列程式碼定義三個衍生自 <xref:System.Windows.Forms.Form> 的類別。  當產生的組件名稱傳遞至上面列表中的可執行檔時，雖然在編譯時期這些類別對裝載的應用程式是未知的，應用程式還是會探索並執行個體化這三個類別。  
  
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
  
## 請參閱  
 [反映](../dotnet/reflection-cpp-cli.md)