//常见功能的ui封装
//兼容性，pc端，手机端，混合app端，微信端
//css为默认样式，如果想要修改则需要在css中加!important
(function(global){
	var _INFO_={
		plug:"AllUi",
		version:'1.0.1'
	},
	defaults={
		menu:{
			nodeID:'',
			position:{},
			itemsFalseColor:'',
			itemsTrueColor:'',
			items:[],
			itemsFalseIcon:[],
			itemsTrueIcon:[],
			style:{}
		}
	};

	function AllUi(options){		
		this.extends(defaults.menu,options);
		this.allUiMenu=defaults.menu;
		this.init();
	};

	AllUi.prototype={
		init:function(){
			this.setCommon(this.allUiMenu.nodeID,this.allUiMenu.position);
		},
		extends:function(){
			for(var i=1;i<arguments.length;i++){
				for(var j in arguments[i]){
					arguments[0][j]=arguments[i][j];
				}
			}
		},
		setCommon:function(nodeID,Aposition){
			var allUiDom=document.getElementById(nodeID)||document.body;
			var allUiBox=document.createElement('div');
			allUiBox.style.position="absolute";
			this.allUiCss(allUiBox,{
				"top":Aposition.top,
				"lef":Aposition.left,
				"bottom":Aposition.bottom,
				"right":Aposition.right
			});
			allUiDom.appendChild(allUiBox);
		},
		allUiCss:function(obj,cssOptions){
			for(var i in cssOptions){
				obj.style[i]=cssOptions[i];		
			}
		}
	};

	global[_INFO_.plug]=AllUi;
})(this)
