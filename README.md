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
		
		
<!--能力检测实现逻辑-->
		<!--检测-->
		var support = {};
			// 在 jq 中不仅判断他是否存在, 还要判断其能力是否符合要求
			
			support.getElementsByClassName = (function () {
				
				var isExist = !!document.getElementsByClassName;
				
				if ( isExist && typeof document.getElementsByClassName == 'function' ) {
					// 自己创建一些元素, 并且加上 class 属性, 看是否可以获得到加上的所有元素
					var div = document.createElement( 'div' ),
						divWithClass = document.createElement( 'div' );
					
					divWithClass.className = 'c';
					div.appendChild( divWithClass );
					return div.getElementsByClassName( 'c' )[ 0 ] === divWithClass;
				
				}
				
				return false;
			})();
			
			
			if ( support.getElementsByClassName ) {
				// return support.getElementsByClassName( className );
				alert( '支持 class' );
			} else {
				// 自己实现( className );
				alert( '不支持 class' );
			}
