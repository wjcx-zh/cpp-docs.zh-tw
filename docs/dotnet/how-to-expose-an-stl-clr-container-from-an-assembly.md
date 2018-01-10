---
title: "如何： 公開 STL/CLR 容器從組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84505edf0877a5ae20d28906dde7f4c709574034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>如何：從組件公開 STL/CLR 容器
STL/CLR 容器，例如`list`和`map`會實作為範本 ref 類別。 C + + 範本會在編譯時期具現化，因為有完全相同的簽章，但位於不同的組件的兩個範本類別是不同類型。 這表示，無法跨組件界限使用的樣板類別。  
  
 若要進行跨組件共用作業，STL/CLR 容器會實作泛型介面<xref:System.Collections.Generic.ICollection%601>。 利用此泛型介面，支援泛型，包括 c + +、 C# 和 Visual Basic 中的所有語言都可以都存取 STL/CLR 容器。  
  
 本主題說明如何顯示寫入名為 c + + 組件中的數個 STL/CLR 容器項目`StlClrClassLibrary`。 我們會示範兩個組件存取`StlClrClassLibrary`。 第一個組件是以 c + + 和 C# 中的第二個撰寫。  
  
 如果兩個組件以 c + + 撰寫，您可以使用來存取容器的泛型介面及其`generic_container`typedef。 例如，如果您有容器的型別`cliext::vector<int>`，則其泛型介面是： `cliext::vector<int>::generic_container`。 同樣地，使用透過泛型介面取得迭代器`generic_iterator`typedef，如下所示： `cliext::vector<int>::generic_iterator`。  
  
 由於這些 typedef 宣告 c + + 標頭檔中，以其他語言撰寫的組件無法使用它們。 因此，若要存取的泛型介面`cliext::vector<int>`在 C# 或任何其他.NET 語言中，使用`System.Collections.Generic.ICollection<int>`。 若要逐一查看這個集合，使用`foreach`迴圈。  
  
 下表列出每一個 STL/CLR 容器會實作泛型介面：  
  
|STL/CLR 容器|泛型介面|  
|------------------------|-----------------------|  
|deque < T\>|ICollection < T\>|  
|hash_map < K，V >|IDictionary < K，V >|  
|hash_multimap < K，V >|IDictionary < K，V >|  
|hash_multiset < T\>|ICollection < T\>|  
|hash_set < T\>|ICollection < T\>|  
|清單 < T\>|ICollection < T\>|  
|對應 < K，V >|IDictionary < K，V >|  
|multimap < K，V >|IDictionary < K，V >|  
|multiset < T\>|ICollection < T\>|  
|設定 < T\>|ICollection < T\>|  
|向量 < T\>|ICollection < T\>|  
  
> [!NOTE]
>  因為`queue`， `priority_queue`，和`stack`容器不支援迭代器，它們不會實作泛型介面，無法存取的跨組件。  
  
## <a name="example-1"></a>範例 1  
  
### <a name="description"></a>描述  
 在此範例中，我們會宣告 c + + 類別，其中包含私用 STL/CLR 成員資料。 然後，我們會宣告授與存取權的私用集合類別的公用方法。 執行作業，在兩個不同的方式，一個用於 c + + 用戶端，其中的其他.NET 用戶端。  
  
### <a name="code"></a>程式碼  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="example-2"></a>範例 2  
  
### <a name="description"></a>描述  
 在此範例中，我們會實作範例 1 中所宣告的類別。 為了讓用戶端使用此類別庫，我們使用資訊清單工具**mt.exe** dll 中內嵌資訊清單檔案。 如需詳細資訊，請參閱程式碼註解。  
  
 如需有關的資訊清單工具和-並存組件的詳細資訊，請參閱[建置 C/c + + 隔離應用程式和-並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。  
  
### <a name="code"></a>程式碼  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example-3"></a>範例 3  
  
### <a name="description"></a>描述  
 在此範例中，我們會建立使用範例 1 和 2 中建立的類別程式庫的 c + + 用戶端。 此用戶端會使用`generic_container`反覆查看之容器，並顯示其內容的 STL/CLR 容器的 typedef。  
  
### <a name="code"></a>程式碼  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="output"></a>輸出  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## <a name="example-4"></a>範例 4  
  
### <a name="description"></a>描述  
 在此範例中，我們會建立使用範例 1 和 2 中建立的類別程式庫的 C# 用戶端。 此用戶端會使用<xref:System.Collections.Generic.ICollection%601>STL/CLR 容器來逐一查看之容器，並顯示其內容的方法。  
  
### <a name="code"></a>程式碼  
  
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
  
### <a name="output"></a>輸出  
  
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
  
## <a name="see-also"></a>請參閱  
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)