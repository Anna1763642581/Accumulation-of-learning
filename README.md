# Accumulation-of-learning
<!--封装单个操作的标签-->
    <!--获取元素标签-->
    var getTag = function ( tag, results ) {
			results = results || [];
			results.push.apply( results, document.getElementsByTagName( tag ) );
			return results;
		};
		
		<!--获取id标签-->
		var getId = function ( id, results ) {
			results = results || [];
			results.push( document.getElementById( id ) );
			return results;
		};
		
		<!--获取className标签-->
		var getClass = function ( className, results ) {
			results = results || [];
			results.push.apply( results, document.getElementsByClassName( className ) );
			return results;
		};
		
		
		
<!--封装选择器类-->
		<!--获取所有的-->
		var get = function ( selector, results ) {
			results = results || [];
			//                     1          2        3       4
			var rquickExpr = /^(?:#([\w-]+)|\.([\w-]+)|([\w]+)|(\*))$/,
				m = rquickExpr.exec( selector );
			
			if ( m ) {
				if ( m[ 1 ] ) {
					results = getId( m[ 1 ], results );
				} else if ( m[ 2 ] ) {
					results = getClass( m[ 2 ], results );
				} else {
					results = getTag( m[ 3 ] || "*", results )
				}；
			}；
			return results;
		};
