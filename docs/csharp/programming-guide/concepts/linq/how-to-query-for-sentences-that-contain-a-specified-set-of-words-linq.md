---
title: "方法: 指定された単語のセットを含む文章を照会する (LINQ) (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c445a70d2f461ea60b575f58e6d57c1edcda922b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>方法 : 指定された単語のセットを含む文章を照会する (LINQ) (C#)
この例は、指定された一連の単語と一致する文言を含む文をテキスト ファイルから検索する方法を示しています。 この例では検索語句の配列をハードコーディングしていますが、実行時に動的に設定することもできます。 この例のクエリを実行すると、"Historically"、"data"、"integrated" という単語をすべて含んだ文が返されます。  
  
## <a name="example"></a>例  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.   
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 このクエリではまず、テキストを文単位に分割し、個々の単語を保持する文字列の配列に分割しています。 その各配列について、重複する単語を <xref:System.Linq.Enumerable.Distinct%2A> メソッドですべて削除したうえで、それらの単語の配列と `wordsToMatch` 配列との <xref:System.Linq.Enumerable.Intersect%2A> 演算を実行します。 共通部分のカウントと `wordsToMatch` 配列のカウントとが一致した場合、文を構成する単語内にすべての検索語句が見つかったものとして判断され、該当する文が返されます。  
  
 句読点を文字列から削除するために、<xref:System.String.Split%2A> の呼び出しでは句読点を区切り記号として使用しています。 この処理がないと、たとえば "Historically," という文字列があった場合に、`wordsToMatch` 配列内の "Historically" と一致しません。 ソース テキストに使われている句読点の種類によっては、別の区切り記号を使う必要があります。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と文字列 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
