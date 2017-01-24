---
title: "如何：從組件公開 STL/CLR 容器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STL/CLR 容器 [STL/CLR]"
  - "STL/CLR, 跨組件問題"
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從組件公開 STL/CLR 容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 容器 \(例如 `list` 和 `map` 會實作為樣板 ref 類別。  由於 C\+\+ 樣板具現化在編譯時期，具有相同的簽章，但兩個樣板類別不同組件實際上是不同的型別。  這表示樣板類別不可跨組件邊界使用。  
  
 使跨組件共用成為可能， STL\/CLR 容器實作 <xref:System.Collections.Generic.ICollection%601>泛型介面。  使用這個泛型介面，支援泛型，包括 C\+\+， C\# 和 Visual Basic 的語言，可以存取 STL\/CLR 容器。  
  
 此主題說明如何在顯示數個以命名為`StlClrClassLibrary` 的C\+\+ 組件撰寫之 STL\/CLR 容器的項目。  會顯示兩個組件存取 `StlClrClassLibrary`。  第一個組件在 C\+\+ 和第二個中以 C\# 撰寫。  
  
 如果兩個組件以 C\+\+ 撰寫，使用其 `generic_container` typedef，存取容器的泛型介面。  例如，在中，如果您有一個容器型別 `cliext::vector<int>`，則它的泛型介面為: `cliext::vector<int>::generic_container`。  同樣地，使用 `generic_iterator` typedef，在中，您可以從泛型介面的 Iterator: `cliext::vector<int>::generic_iterator`。  
  
 因為這些 Typedef 在 C\+\+ 標頭檔宣告，其他語言撰寫的組件無法使用。  因此，存取的 `cliext::vector<int>` 泛型介面在 C\# 或其他 .NET 語言，請使用 `System.Collections.Generic.ICollection<int>`。  若要逐一查看此集合，請使用 `foreach` 迴圈。  
  
 下表列出泛型介面的每個 STL\/CLR 容器實作:  
  
|STL\/CLR 容器|Generic Interface \- 泛型介面|  
|-----------------|-------------------------------|  
|dequeT\<T\>|ICollection\<T\>|  
|hash\_mapK\<K, V\>|IDictionary\<K, V\>|  
|hash\_multimap\<K, V\>|IDictionary\<K, V\>|  
|hash\_multiset\<T\>|ICollection\<T\>|  
|hash\_set\<T\>|ICollection\<T\>|  
|list\<T\>|ICollection\<T\>|  
|map\<K, V\>|IDictionary\<K, V\>|  
|multimap\<K, V\>|IDictionary\<K, V\>|  
|multiset\<T\>|ICollection\<T\>|  
|set\<T\>|ICollection\<T\>|  
|vector\<T\>|ICollection\<T\>|  
  
> [!NOTE]
>  由於 `queue`、 `priority_queue`和 `stack` 容器不支援 Iterator，它們不實作泛型介面，也無法存取的跨組件。  
  
## 範例 1  
  
### 說明  
 在此範例中，我們宣告 C \+\+. 類別包含 STL\/CLR 私用成員資料。  我們然後宣告公用方法加入至類別的私人收集的授權存取。  我們以兩種不同的方式，將 C\+\+ 用戶端使用和其他 .NET 用戶端的。  
  
### 程式碼  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## 範例 2  
  
### 說明  
 在此範例中，我們會實作在範例宣告類別 1. 中。  為了讓用戶端可以使用這個類別庫，我們使用資訊清單工具 **mt.exe** 嵌入資訊清單檔的 DLL。  如需詳細資訊，請參閱程式碼註解。  
  
 如需資訊清單工具和並存組件的詳細資訊，請參閱 [建置 C\/C\+\+ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。  
  
### 程式碼  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## 範例 3  
  
### 說明  
 在此範例中，我們會在範例 1 和 2. 使用建立的類別庫的 C \+\+. 用戶端。  這個用戶端使用 STL\/CLR 容器的 `generic_container` typedef 逐一查看容器並顯示其內容。  
  
### 程式碼  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### Output  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## 範例 4  
  
### 說明  
 在此範例中，我們會在範例 1 和 2. 使用建立的類別庫的 C\# 用戶端。  這個用戶端使用 STL\/CLR 容器的 <xref:System.Collections.Generic.ICollection%601> 方法逐一查看容器並顯示其內容。  
  
### 程式碼  
  
```  
// CsConsoleApp.cs  
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll  
  
using System;  
using System.Collections.Generic;  
using StlClrClassLibrary;  
using cliext;  
  
namespace CsConsoleApp  
{  
    class Program  
    {  
        static int Main(string[] args)  
        {  
            StlClrClass theClass = new StlClrClass();  
  
            Console.WriteLine("cliext::deque contents:");  
            ICollection<char> iCollChar = theClass.GetDequeCs();  
            foreach (char c in iCollChar)  
            {  
                Console.WriteLine(c);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::list contents:");  
            ICollection<float> iCollFloat = theClass.GetListCs();  
            foreach (float f in iCollFloat)  
            {  
                Console.WriteLine(f);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::map contents:");  
            IDictionary<int, string> iDict = theClass.GetMapCs();  
            foreach (KeyValuePair<int, string> kvp in iDict)  
            {  
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::set contents:");  
            ICollection<double> iCollDouble = theClass.GetSetCs();  
            foreach (double d in iCollDouble)  
            {  
                Console.WriteLine(d);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::vector contents:");  
            ICollection<int> iCollInt = theClass.GetVectorCs();  
            foreach (int i in iCollInt)  
            {  
                Console.WriteLine(i);  
            }  
            Console.WriteLine();  
  
            return 0;  
        }  
    }  
}  
```  
  
### Output  
  
```  
cliext::deque contents:  
a  
b  
  
cliext::list contents:  
3.14159  
2.71828  
  
cliext::map contents:  
0 Hello  
1 World  
  
cliext::set contents:  
2.71828  
3.14159  
  
cliext::vector contents:  
10  
20  
```  
  
## 請參閱  
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)