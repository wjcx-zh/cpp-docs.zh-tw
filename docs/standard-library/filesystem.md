---
title: '&lt;filesystem&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
dev_langs:
- C++
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 4cb454ca6ea92ede5c4cf83c1072e22e60577811
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;
包含用於存取類別和函式的標頭 \<filesystem>，以操作並擷取路徑、檔案和目錄的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#include <experimental/filesystem> // C++-standard header file name  
#include <filesystem> // Microsoft-specific implementation header file name  
using namespace std::experimental::filesystem::v1;  
```  
  
> [!IMPORTANT]
>  在 Visual Studio 2017 版本中，\<experimental/filesystem> 標頭還不是 C++ 標準。 Visual C++ 2017 實作的是 [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf) 中的草稿最終版標準。  
  
 這個標頭支援兩個廣泛的主機作業系統類別之一的檔案系統：Microsoft Windows 和 Posix。  
  
 雖然大部分功能對這兩個作業系統而言是共通的，不過本文還是指出其中的差異。 例如:   
  
-   Windows 支援多個根名稱，例如 c: 或 \\\network_name。 檔案系統是由樹狀樹系所組成，每個樹狀目錄有自己的根目錄 (例如 c:\ 或 \\\network_name\\) 與目前的目錄，以完成相對路徑名稱 (而非絕對路徑名稱)。  
  
-   Posix 支援不含根目錄名稱的單一樹狀目錄、單一根目錄 / 和單一目前目錄。  
  
 另一項重大差異是路徑名稱的原生表示法：  
  
-   Windows 使用以 Null 終止的 wchar_t 序列，並編碼為 UTF-16 (每個字元有一或兩個元素)。  
  
-   Posix 使用以 Null 終止的 char 序列，並編碼為 UTF-8 (每個字元有一或多個元素)。  
  
-   類別路徑物件以原生格式來儲存路徑名稱，但可輕鬆地在這個預存格式和幾個外部格式之間進行轉換：  
  
    -   以 Null 終止的 char 序列，並採用作業系統偏好的方式進行編碼。  
  
    -   以 Null 終止的 char 序列，並編碼為 UTF-8。  
  
    -   以 Null 終止的 wchar_t 序列，並採用作業系統偏好的方式進行編碼。  
  
    -   以 Null 終止的 char16_t 序列，並編碼為 UTF-16。  
  
    -   以 Null 終止的 char32_t 序列，並編碼為 UTF-32。  
  
 請視需要考慮使用一或多個 `codecvt` Facet，在這些表示法之間進行轉換。 如果未指定特定地區設定物件，則會從全域地區設定取得這些 Facet。  
  
 另一項差異是每個作業系統讓您用來指定檔案或目錄存取權限的詳細資料：  
  
1.  Windows 會記錄檔案是唯讀或可寫入，以及對目錄而言沒有意義的屬性。  
  
2.  Posix 會記錄檔案可讀取、寫入或執行 (如果是目錄則記錄可否掃描)；執行這些權限的人員為擁有者、擁有者群組或所有人；以及其他一些權限。  
  
 這兩個系統在根目錄名稱之後有通用的路徑名稱結構。 路徑名稱若為 c:/abc/xyz/def.ext：  
  
-   根名稱為 c:。  
  
-   根目錄為 /。  
  
-   根路徑為 c:/。  
  
-   相對路徑為 abc/xyz/def.ext。  
  
-   父路徑為 c:/abc/xyz。  
  
-   檔案名稱為 def.ext。  
  
-   主體為 def。  
  
-   副檔名為 .ext。  
  
 一項較不重要的差異是路徑名稱中目錄序列之間的 **慣用分隔符號**。 這兩個作業系統可讓您撰寫正斜線 /，但在某些內容中，Windows 偏好使用反斜線 \\。  
  
 最後，path 物件的一項重要功能是，每當標頭 \<fstream> 中定義的類別需要 filename 引數時，您都可以使用這些物件。  
  
 如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。  
  
## <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[directory_entry 類別](../standard-library/directory-entry-class.md)|描述 `directory_iterator` 或 `recursive_directory_iterator` 傳回的物件，且物件中包含路徑。|  
|[directory_iterator 類別](../standard-library/directory-iterator-class.md)|描述可循序遍訪檔案系統目錄中的檔案名稱的輸入迭代器。|  
|[filesystem_error 類別](../standard-library/filesystem-error-class.md)|擲回例外狀況的基底類別，以報告低階系統溢位。|  
|[path 類別](../standard-library/path-class.md)|定義一個類別，以儲存適合做為檔案名稱之樣板類型 `String` 的物件。|  
|[recursive_directory_iterator 類別](../standard-library/recursive-directory-iterator-class.md)|描述可循序遍訪檔案系統目錄中的檔案名稱的輸入迭代器。 迭代器也可以下降到子目錄。|  
|[file_status 類別](../standard-library/file-status-class.md)|包裝 `file_type`。|  
  
## <a name="structs"></a>結構  
  
|名稱|說明|  
|----------|-----------------|  
|[space_info 結構](../standard-library/space-info-structure.md)|保留磁碟區的相關資訊。|  
  
## <a name="functions"></a>函式  
 [\<filesystem> 函式](../standard-library/filesystem-functions.md)  
  
## <a name="operators"></a>運算子  
 [\<filesystem> 運算子](../standard-library/filesystem-operators.md)  
  
## <a name="enumerations"></a>列舉  
  
|名稱|說明|  
|----------|-----------------|  
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|列舉搭配使用 [copy_file](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) ，並在已存在目的地檔案時決定行為。|  
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|指定目錄迭代器之選項的列舉。|  
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|檔案類型的列舉。|  
|[權限](../standard-library/filesystem-enumerations.md#perms)|用來傳達權限和權限選項的位元遮罩類型|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)




