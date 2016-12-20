---
title: "初始化陣列 | Microsoft Docs"
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
helpviewer_keywords: 
  - "初始化陣列"
  - "初始化陣列 [c + +]"
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始化陣列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果類別具有建構函式，該類別的陣列會以建構函式進行初始化。 如果初始設定式清單中的項目少於陣列中的元素數目，則其餘元素會使用預設建構函式。 如果該類別未定義預設建構函式，則初始設定式清單必須完整，也就是說，陣列中的每個元素都必須有一個初始設定式。  
  
 以定義兩個建構函式的 `Point` 類別為例：  
  
```  
// initializing_arrays1.cpp  
class Point  
{  
public:  
   Point()   // Default constructor.  
   {  
   }  
   Point( int, int )   // Construct from two ints  
   {  
   }  
};  
  
// An array of Point objects can be declared as follows:  
Point aPoint[3] = {  
   Point( 3, 3 )     // Use int, int constructor.  
};  
  
int main()  
{  
}  
```  
  
 `aPoint` 的第一個元素是使用 `Point( int, int )` 建構函式建構，其餘兩個元素則是使用預設建構函式建構。  
  
 靜態成員陣列 (是否 **const** 與否) 可以 （在類別宣告之外），其定義中初始化。 例如:   
  
```  
// initializing_arrays2.cpp  
class WindowColors  
{  
public:  
    static const char *rgszWindowPartList[7];  
};  
  
const char *WindowColors::rgszWindowPartList[7] = {  
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",  
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [(NOTINBUILD)特殊成員函式](http://msdn.microsoft.com/zh-tw/82223d73-64cb-4923-b678-78f9568ff3ca)