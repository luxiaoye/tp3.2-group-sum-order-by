# tp3.2-group-sum-order-by
//分组并计算每组数据中某列数据的和，然后按最新数据id排序

public function share_a(){


        $new['field']='奖励收益';
        $model=M('tablename');
        //先按最新的排序，得到sql语句
        $subQuery = $model->field('field')->join('如果有表需要关联的情况下，若无，去掉')->table('tablename')->where($new)->order('field desc')->buildSql();
        
        //拼接下面语句，合并自己要合并的id相同的数据，然后再次按自己的需要排序，share是取表的别名,order里的排序字段，上面的field必须要有
        $ab=$model->table($subQuery.' share')->group('合并的字段')->order('money_bill_id desc')->limit(20)->select();
        var_dump($ab);

    }
    
//分组计算列值
    public function share_b(){
    
    
    
         $new['field']='奖励收益';
        $model=M('tablename');
       $subQuery = $model->field('field')->join('如果有表需要关联的情况下，若无，去掉')->table('tablename')->where($new)->order('field desc')->buildSql();
       
        //求和
        $ab=$model->field('sum(求和的字段) money_sum,user_nickname,money_bill_id,money_bill_date,t_user_user_id')->table($subQuery.' share')->group('合并的字段')->order('money_bill_id desc')->limit(20)->select();
        var_dump($ab);

    }
