# closure_cascading

Welcome to the closure_cascading wiki!

# is(1)(2)(3)(4)
## ~(2)(3)(4)(2)(3)(4) loop
<dl>
  <dt>(1)</dt>
  <dd>object in oder to compare (2)</dd>
  <dt>(2)</dt>
  <dd>Comparison if</dd>
  <dd> type is String it is compare to Object name of (1)</dd>
  <dd>type is boolean which is to check Null of (1)</dd>
  <dt>(3)</dt>
  <dd>function if condition is true</dd>
  <dt>(4)</dt>
  <dd>function if condition is false</dd>
</dl>


```javascript:is.js
var is = function(c){
    return function(sss){
        var ss=Object.prototype.toString.call(c).slice(8, -1);
        var type=typeof sss;
        var b = (type=="boolean")?(c!=null):(sss==ss);
        return function(f){
            (b==true)?f.apply(c,[c,ss,sss]):0;
            return function(ff){
                (b==false)?((ff)?ff.apply(c,[c,ss,sss]):0):0;
                return is(c);
            };
        }
    }
};
is(1)("Number")
    (function(c,ss,sss){console.log(c,"is",sss)})
is("1")("Number")
    (function(c,ss,sss){console.log(c,"is",sss)})
    (function(c,ss,sss){console.log(c,"is not",sss)})
```

