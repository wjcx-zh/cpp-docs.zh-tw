---
title: "編譯器警告 (層級 1) C4462 | Microsoft Docs"
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
  - "C4462"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4462"
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4462
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法判斷類型的 GUID。程式可能在執行階段失敗。  
  
 警告 C4462 當公用 `TypedEventHandler` 的其中一個類型參數做為封入類別的參考時，Windows 執行階段應用程式或元件中就會發生警告 C4462。  
  
 **這種程式碼會引發警告：**  
  
```  
namespace N  
{  
       public ref struct EventArgs sealed {};  
       public ref struct R sealed  
       {  
              R() {}  
              event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
       };  
}  
  
[Platform::MTAThread]  
int main()  
{  
     auto x = ref new N::R();  
}  
  
```  
  
 **若要修正錯誤：**  
  
 有兩種方式可以解決此錯誤。  一種方式是指定事件內部存取範圍，讓相同可執行檔中的程式碼可以使用，但不對其他 Windows 執行階段元件中的程式碼提供，如下一個範例中所示。  
  
```  
  
internal:  
event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
  
```  
  
 如果事件必須為公用，則您可以使用另一種解決方法，也就是透過預設介面將它公開：  
  
```  
  
ref struct R;  
public interface struct IR { event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e; };  
  
public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR  
{  
    R() {}  
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
};  
  
```  
  
 只有在從另一個元件存取 `Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^` 類型時，才會使用該類型的 GUID。  第一個解決方法有效，是因為解決後只能從它自己的元件內存取。  否則，編譯器必須假設最糟情況並發出警告。