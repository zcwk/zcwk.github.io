---
layout: post
title: Android DataBinding需要注意的地方
category: Android
tags: Android DataBinding需要注意的地方
keywords: Android DataBinding需要注意的地方
---


## 在RecycleView 的 adapter中使用databinding
``` java
	@Override
    public RecyclerView.ViewHolder onCreateViewHolder(ViewGroup parent, int viewType)
    {
        ItemUserBinding binding = DataBindingUtil.inflate(LayoutInflater.from(this.context), R.layout.item_user, parent, false);
        return new UserViewHolder(binding.getRoot());
    }

    @Override
    public void onBindViewHolder(RecyclerView.ViewHolder holder, int position)
    {
        ItemUserBinding binding = DataBindingUtil.getBinding(holder.itemView);
        binding.setModel(this.items.get(position));
        binding.executePendingBindings();
    }
```

