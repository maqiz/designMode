# designMode
javascript之设计模式

		//函数柯里化
		function curry(fn){
			var args = Array.prototype.slice.call(arguments,1);
			return function(){
				var innerArgs = Array.prototype.slice.call(arguments);
				var findArgs = args.concat(innerArgs);
				return fn.apply(this,findArgs);
			}
		}
		function add(num1,num2,num3){
			return num1+num2+num3;
		}
		var t = curry(add,50)(1,2);
		alert(t);
      
      
		//单例模式
		var xiaowang = (function(argument){
			var xiaowangjia =function(message){
				this.menling =message;
			}
			var men;
			var info = {
				sendMessage:function(message){
					if(!men){
						men = new xiaowangjia(message);
					};
					return men;
				}
			}
			return info;
		})();
		var xiaoli = {
			callXiaowang:function(msg){
				var _xw = xiaowang.sendMessage(msg);
				alert(_xw.menling);
				_xw = null;
			}
		}
		xiaoli.callXiaowang('didi');
		
		//构造函数
		function Createdoor(huawen){
			if(!(this instanceof Createdoor)){
				return new Createdoor(huawen);
			}
			this.suo = "普通";
			this.huawen = huawen ? huawen : "普通";
			this.create = function(){
				return "锁"+this.suo+"花纹"+this.huawen;
			}
		}
		var xiaozhang = new Createdoor("dd");
		var xiaoli = new Createdoor();
		console.log(xiaozhang.create());
