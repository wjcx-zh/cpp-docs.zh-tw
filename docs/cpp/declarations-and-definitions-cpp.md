---
title: "宣告和定義 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 宣告和定義 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[宣告](http://msdn.microsoft.com/zh-tw/2fd0cddb-b64c-4c9f-9aac-9f8e7ef892f4)在程式中引進名稱 \(例如變數、命名空間、函式和類別的名稱\)。  宣告也會指定類型資訊，以及所宣告物件的其他特性。  名稱必須先宣告才能使用；在 C\+\+ 中，名稱的宣告位置可決定編譯器是否可以看到它。  您不能參考編譯單位中後面某個位置所宣告的函式或類別；您可以使用*「向前宣告」*\(Forward Declaration\) 來克服這項限制。  
  
 [定義](http://msdn.microsoft.com/zh-tw/f96e2c0d-abb5-4414-9ea1-4d5b4048d50a)則會指定名稱所描述的程式碼或資料。  編譯器需要有定義，才能針對所宣告的項目配置儲存空間。  
  
## 宣告  
 宣告會將一個或多個名稱引入程式。  宣告在程式中可能會出現一次以上。  因此，您可以為每個編譯單位宣告類別、結構、列舉類型和其他使用者定義類型。  多重宣告的條件約束是，所有宣告必須相同。  宣告也可當做定義，但宣告如有下列情況則除外：  
  
1.  為函式原型 \(沒有函式主體的函式宣告\)。  
  
2.  包含 `extern` 指定名稱，但不包含初始設定式 \(物件和變數\) 或函式主體 \(函式\)。  這表示此定義不一定會位於目前的轉譯單位中，並提供外部連結的名稱。  
  
3.  為類別宣告內的靜態資料成員。  
  
     由於靜態類別資料成員是由類別中所有物件共用的不連續變數，因此必須在類別宣告之外定義及初始化。  \(如需類別和類別成員的詳細資訊，請參閱[類別](../cpp/classes-and-structs-cpp.md)\)。  
  
4.  為不含下列定義的類別名稱宣告，例如 `class T;`。  
  
5.  為 `typedef` 陳述式。  
  
 宣告也可做為定義的範例如下：  
  
```  
// Declare and define int variables i and j.  
int i;  
int j = 10;  
  
// Declare enumeration suits.  
enum suits { Spades = 1, Clubs, Hearts, Diamonds };  
  
// Declare class CheckBox.  
class CheckBox : public Control  
{  
public:  
            Boolean IsChecked();  
    virtual int     ChangeState() = 0;  
};  
```  
  
 某些不是定義的宣告如下：  
  
```  
  
extern int i;  
char *strchr( const char *Str, const char Target );  
```  
  
 名稱會視為在緊接著它的宣告子之後、但是在它的 \(選擇性\) 初始設定式之前宣告   如需詳細資訊，請參閱[宣告點](../cpp/point-of-declaration-in-cpp.md)。  
  
 宣告會發生在*「範圍」*\(scope\) 內。  範圍可控制項所宣告的名稱可見性，以及所定義的物件持續時間 \(若有的話\)。  如需範圍規則如何與宣告互動的詳細資訊，請參閱[範圍](../cpp/scope-visual-cpp.md)。  
  
 物件宣告也是定義，除非其包含`extern`儲存類別規範中描述的 [儲存類別規範。](http://msdn.microsoft.com/zh-tw/10b3d22d-cb40-450b-994b-08cf9a211b6c) 函式宣告也是定義，除非其為原型。  原型是不含定義函式主體的函式標頭。  物件的定義會促使儲存體配置，並為該物件進行適當的初始化。  
  
## 定義  
 定義為物件或變數、函式、類別或列舉程式的唯一規格。  由於定義必須是唯一的，因此程式中只能包含一個特定程式項目的定義。  宣告和定義之間可以有多對一的對應關係。  在兩種情況下可以宣告但未定義程式項目：  
  
1.  已宣告但永遠不會使用函式呼叫或使用接受函式位址的運算式參考的函式。  
  
2.  只有在不知道其定義時才使用的類別。  不過，該類別必須進行宣告。  下列程式碼說明此情況：  
  
    ```  
    // definitions.cpp  
    class WindowCounter;   // Forward declaration; no definition  
  
    class Window  
    {  
       // Definition of WindowCounter not required  
       static WindowCounter windowCounter;  
    };  
  
    int main()  
    {  
    }  
    ```  
  
## 請參閱  
 [基本概念](../cpp/basic-concepts-cpp.md)   
 [宣告點](../cpp/point-of-declaration-in-cpp.md)