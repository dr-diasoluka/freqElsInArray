# freqElsInArray
How many different elements does an array contain, and what the frequency of each different element

    <script type="text/javascript">"use strict";

      /********************************************************/
      /********************************************************/
      /**/ Array.prototype.freqElsInArr = function(...p) {
      /**/   let retVal = [...new Set(this)].map(x=>{
      /**/     return {el:x,freq:(this.filter(y=>x==y).length)}
      /**/   });
      /********************************************************/
      /********************************************************/

      /********************************************************/
      //
      // returning the frequencies to the callee.
      //
      /********************************************************/
         let sortArray=[] ,
             s = p.length ? p : p.concat("sByElFreq") ,
             t ;
         console.log("Sorted by " , s);
         // Sorted by Array(3) [ "sByElName", "nat", "sByElFreq" ]



         if(s.includes(t="sByElName") || s.includes(t="sByElFreq") || s.includes(t="nat")) {
            if(s.includes(t="nat")) sortArray.push([t,retVal]);

            if(s.includes(t="sByElName")) {
                sortArray.push([t,[...retVal].sort((a,z)=>a["el"]-z["el"])])
            };

            if(s.includes(t="sByElFreq")) {
                sortArray.push([t,[...retVal].sort((a,z)=>a["freq"]-z["freq"])])
            };
         };

         return sortArray;
      }
      /********************************************************/
      /********************************************************/


      //////////////////////////////////////////


       const ourArr = [];
       for(let k=0 ; k<30 ; k++) ourArr.push(Math.round(Math.random()*10));

       console.log("Our Initial Array =");
       console.log(ourArr.join(" | "),"\n");

      // Our Initial Array =
      // 4 | 8 | 3 | 2 | 2 | 7 | 9 | 7 | 2 | 2 | 4 | 7 | 6 | 6 | 4 | 1 | 9 | 7 | 7 | 6 | 4 | 4 | 3 | 1 | 8 | 6 | 6 | 7 | 6 | 7


      console.log("\nFréq of Each el in Array :");


      /********************************************************/
      /********************************************************/
      /**/
      /**/  //          THE CALL
      /**/
      /**/  const els = ourArr.freqElsInArr ( "sByElName" , "nat" , "sByElFreq" );
      /**/  //const els = ourArr.freqElsInArr (  );
      /**/  //const els = ourArr.freqElsInArr ( "sByElName" );
      /**/
      /********************************************************/
      /********************************************************/


      /********************************************************/
      /********************************************************/
      /**/
      console.log("\n***** FOR A SIMPLE LIST *****\n");
      /**/
      /**/    els.forEach(x => {
      /**/         console.log ( x [0] );
      /**/         let list = x[1].map(z =>
      /**/                    z["el"] + ": " + z["freq"] + " fois"
      /**/         ).join(" | ");
      /**/         console.log(list);
      /**/    });
      /**/
      /********************************************************/
      /********************************************************/

      // ***** FOR A SIMPLE LIST *****
      //
      // nat
      //    4: 5 fois | 8: 2 fois | 3: 2 fois | 2: 4 fois | 7: 7 fois | 9: 2 fois | 6: 6 fois | 1: 2 fois
      //
      // sByElName
      //    1: 2 fois | 2: 4 fois | 3: 2 fois | 4: 5 fois | 6: 6 fois | 7: 7 fois | 8: 2 fois | 9: 2 fois
      //
      // sByElFreq
      //    8: 2 fois | 3: 2 fois | 9: 2 fois | 1: 2 fois | 2: 4 fois | 4: 5 fois | 6: 6 fois | 7: 7 fois




      console.log("\n***** FOR FURTHER MANIPULATION *****\n");

      /********************************************************/
      /********************************************************/
      /**/
      /**/  els.forEach(x => console.log ( x[0] , x[1] ));
      /**/
      /********************************************************/
      /**/
      /**/  els.forEach(x =>
      /**/    console.log ( "Sort:",x[0] , "\n" +
      /**/       x[1].map( (y,idx) =>
      /**/         `${idx.toString().padStart(2," ")}:`+
      /**/             `Object { el: ${String(y["el"]).padStart(2," ")}`+
      /**/             `, freq: ${y["freq"]} }`
      /**/       ).join("\n")
      /**/    )
      /**/  );
      /**/
      /********************************************************/
      /********************************************************/

      // test.html:119:38
      // nat            Array(8) [ {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…} ]
      // 0: Object { el: 4, freq: 5 }
      // 1: Object { el: 8, freq: 2 }
      // 2: Object { el: 3, freq: 2 }
      // 3: Object { el: 2, freq: 4 }
      // 4: Object { el: 7, freq: 7 }
      // 5: Object { el: 9, freq: 2 }
      // 6: Object { el: 6, freq: 6 }
      // 7: Object { el: 1, freq: 2 }
      // length: 8
      // <prototype>: Array []
      //
      // test.html:119:38
      // sByElName      Array(8) [ {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…} ]
      // 0: Object { el: 1, freq: 2 }
      // 1: Object { el: 2, freq: 4 }
      // 2: Object { el: 3, freq: 2 }
      // 3: Object { el: 4, freq: 5 }
      // 4: Object { el: 6, freq: 6 }
      // 5: Object { el: 7, freq: 7 }
      // 6: Object { el: 8, freq: 2 }
      // 7: Object { el: 9, freq: 2 }
      // length: 8
      // <prototype>: Array []
      //
      // test.html:119:38
      // sByElFreq      Array(8) [ {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…} ]
      // 0: Object { el: 8, freq: 2 }
      // 1: Object { el: 3, freq: 2 }
      // 2: Object { el: 9, freq: 2 }
      // 3: Object { el: 1, freq: 2 }
      // 4: Object { el: 2, freq: 4 }
      // 5: Object { el: 4, freq: 5 }
      // 6: Object { el: 6, freq: 6 }
      // 7: Object { el: 7, freq: 7 }
      // length: 8
      // <prototype>: Array []


      // test.html:122:23    Sort: nat
      //  0:Object { el:  4, freq: 5 }
      //  1:Object { el:  8, freq: 2 }
      //  2:Object { el:  3, freq: 2 }
      //  3:Object { el:  2, freq: 4 }
      //  4:Object { el:  7, freq: 7 }
      //  5:Object { el:  9, freq: 2 }
      //  6:Object { el:  6, freq: 6 }
      //  7:Object { el:  1, freq: 2 }
      //
      // test.html:122:23    Sort: sByElName
      //  0:Object { el:  1, freq: 2 }
      //  1:Object { el:  2, freq: 4 }
      //  2:Object { el:  3, freq: 2 }
      //  3:Object { el:  4, freq: 5 }
      //  4:Object { el:  6, freq: 6 }
      //  5:Object { el:  7, freq: 7 }
      //  6:Object { el:  8, freq: 2 }
      //  7:Object { el:  9, freq: 2 }
      //
      // test.html:122:23    Sort: sByElFreq
      //  0:Object { el:  8, freq: 2 }
      //  1:Object { el:  3, freq: 2 }
      //  2:Object { el:  9, freq: 2 }
      //  3:Object { el:  1, freq: 2 }
      //  4:Object { el:  2, freq: 4 }
      //  5:Object { el:  4, freq: 5 }
      //  6:Object { el:  6, freq: 6 }
      //  7:Object { el:  7, freq: 7 } test.html:121:23
    </script>


All the outputs to the console, from another execution

test.html:64:16
Our Initial Array =

test.html:65:16
9 | 2 | 5 | 7 | 6 | 6 | 9 | 6 | 1 | 3 | 7 | 9 | 2 | 2 | 7 | 2 | 2 | 9 | 6 | 5 | 2 | 7 | 6 | 2 | 8 | 4 | 9 | 5 | 7 | 2

test.html:72:15
Fréq of Each el in Array :

test.html:33:18
Sorted by Array(3) [ "sByElName", "nat", "sByElFreq" ]


test.html:90:15
***** FOR A SIMPLE LIST *****

test.html:93:28  nat
test.html:97:28
9: 5 fois | 2: 8 fois | 5: 3 fois | 7: 5 fois | 6: 5 fois | 1: 1 fois | 3: 1 fois | 8: 1 fois | 4: 1 fois

test.html:93:28  sByElName
test.html:97:28
1: 1 fois | 2: 8 fois | 3: 1 fois | 4: 1 fois | 5: 3 fois | 6: 5 fois | 7: 5 fois | 8: 1 fois | 9: 5 fois

test.html:93:28  sByElFreq
test.html:97:28
1: 1 fois | 3: 1 fois | 8: 1 fois | 4: 1 fois | 5: 3 fois | 9: 5 fois | 7: 5 fois | 6: 5 fois | 2: 8 fois

test.html:117:15
***** FOR FURTHER MANIPULATION *****

test.html:122:38       nat
Array(9) [ {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…} ]
  0: Object { el: 9, freq: 5 }
  1: Object { el: 2, freq: 8 }
  2: Object { el: 5, freq: 3 }
  3: Object { el: 7, freq: 5 }
  4: Object { el: 6, freq: 5 }
  5: Object { el: 1, freq: 1 }
  6: Object { el: 3, freq: 1 }
  7: Object { el: 8, freq: 1 }
  8: Object { el: 4, freq: 1 }
  length: 9
  <prototype>: Array []

test.html:122:38       sByElName
Array(9) [ {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…} ]
  0: Object { el: 1, freq: 1 }
  1: Object { el: 2, freq: 8 }
  2: Object { el: 3, freq: 1 }
  3: Object { el: 4, freq: 1 }
  4: Object { el: 5, freq: 3 }
  5: Object { el: 6, freq: 5 }
  6: Object { el: 7, freq: 5 }
  7: Object { el: 8, freq: 1 }
  8: Object { el: 9, freq: 5 }
  length: 9
  <prototype>: Array []

test.html:122:38       sByElFreq
Array(9) [ {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…} ]
  0: Object { el: 1, freq: 1 }
  1: Object { el: 3, freq: 1 }
  2: Object { el: 8, freq: 1 }
  3: Object { el: 4, freq: 1 }
  4: Object { el: 5, freq: 3 }
  5: Object { el: 9, freq: 5 }
  6: Object { el: 7, freq: 5 }
  7: Object { el: 6, freq: 5 }
  8: Object { el: 2, freq: 8 }
  length: 9
  <prototype>: Array []


test.html:127:23    Sort: nat
 0:Object { el:  9, freq: 5 }
 1:Object { el:  2, freq: 8 }
 2:Object { el:  5, freq: 3 }
 3:Object { el:  7, freq: 5 }
 4:Object { el:  6, freq: 5 }
 5:Object { el:  1, freq: 1 }
 6:Object { el:  3, freq: 1 }
 7:Object { el:  8, freq: 1 }
 8:Object { el:  4, freq: 1 }

test.html:127:23    Sort: sByElName
 0:Object { el:  1, freq: 1 }
 1:Object { el:  2, freq: 8 }
 2:Object { el:  3, freq: 1 }
 3:Object { el:  4, freq: 1 }
 4:Object { el:  5, freq: 3 }
 5:Object { el:  6, freq: 5 }
 6:Object { el:  7, freq: 5 }
 7:Object { el:  8, freq: 1 }
 8:Object { el:  9, freq: 5 }

test.html:127:23    Sort: sByElFreq
 0:Object { el:  1, freq: 1 }
 1:Object { el:  3, freq: 1 }
 2:Object { el:  8, freq: 1 }
 3:Object { el:  4, freq: 1 }
 4:Object { el:  5, freq: 3 }
 5:Object { el:  9, freq: 5 }
 6:Object { el:  7, freq: 5 }
 7:Object { el:  6, freq: 5 }
 8:Object { el:  2, freq: 8 }
