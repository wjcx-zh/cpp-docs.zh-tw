---
title: "directory_iterator 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator
- FILESYSTEM/std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- FILESYSTEM/std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::increment
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator=
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator==
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator!=
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator*
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator->
- std::experimental::filesystem::directory_iterator::operator->
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator++
- std::experimental::filesystem::directory_iterator::operator++
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4eb80d5309a7749c1374d72be16798dbeea33bdc
ms.lasthandoff: 02/24/2017

---
# <a name="directoryiterator-class"></a>directory_iterator 類別
描述可循序遍訪目錄中的檔案名稱的輸入迭代器。 對於迭代器 X，運算式 *X 會評估為 directory_entry 類別的物件，該物件會包裝檔案名稱及其狀態的任何已知項目。  
  
 類別會儲存類型路徑物件，這裡稱之為 mydir 用於展示，代表要排序的目錄名稱，而稱之為 myentry 的類型 directory_entry 物件，代表目前的目錄順序檔案名稱。 預設的類型 directory_entry 建構物件具有空的 mydir 路徑名稱，表示序列結尾迭代器。  
  
 例如，假設目錄 abc 有項目 def 和 ghi，程式碼：  
  
 `for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`  
  
 用引數 path("abc/def") 與 path("abc/ghi") 呼叫 visit 。  
  
 如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class directory_iterator;  
```  
  
## <a name="directoryiteratordirectoryiterator"></a>directory_iterator::directory_iterator  
  
```  
directory_iterator() noexcept;  
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;  
directory_iterator(const directory_iterator&) = default;  
directory_iterator(directory_iterator&&) noexcept = default;  
```  
  
 第一個建構函式會產生序列結尾迭代器。 第二個和第三個建構函式將 pval 存入 mydir，然後嘗試開啟並讀取 mydir 為目錄。 如果成功的話，它們會把第一個檔名儲存在 myentry 的目錄中；否則會產生序列結尾迭代器。  
  
 預設建構函式會如預期般運作。  
  
## <a name="directoryiteratorincrement"></a>directory_iterator::increment  
  
```  
directory_iterator& increment(error_code& ec) noexcept;  
```  
  
 此函式會嘗試前進到目錄中的下一個檔案名稱。 如果成功，則會在 myentry 中儲存該檔案名稱，否則會產生序列結尾迭代器。  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator!=  
  
```  
bool operator!=(const directory_iterator& right) const;
```  
  
 此成員運算子會傳回 !(*this == right)。  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator=  
  
```  
directory_iterator& operator=(const directory_iterator&) = default;  
directory_iterator& operator=(directory_iterator&&) noexcept = default;  
```  
  
 預設成員指派運算子會如預期般運作。  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator==  
  
```  
bool operator==(const directory_iterator& right) const;
```  
  
 只有在 *this 和 right 都是或都不是序列結尾迭代器時，此成員運算子才會傳回 true。  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator*  
  
```  
const directory_entry& operator*() const;
```  
  
 此成員運算子會傳回 myentry。  
  
## <a name="directoryiteratoroperator-"></a>directory_iterator::operator->  
  
```  
const directory_entry * operator->() const;
```  
  
 成員函式傳回 &**this。  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator++  
  
```  
directory_iterator& operator++();
directory_iterator& operator++(int);
```  
  
 第一個成員函式會呼叫 increment()，然後傳回 *this。 第二個成員函式會複製物件、呼叫 increment()，然後傳回複本。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<experimental/filesystem>  
  
 **命名空間：**std::experimental::filesystem  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)


