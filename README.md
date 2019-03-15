# timezone_shapefiles

[https://traveladdicts.unli.xyz/guestblog/timezone-shapefiles](https://traveladdicts.unli.xyz/guestblog/timezone-shapefiles)

data extracted from [who's on first](https://github.com/whosonfirst-data/whosonfirst-data/blob/master/LICENSE.md)

```
select 
replace(group_concat( distinct e.name || ','),',,',',') n,
a.id,
a.parent_id,
a.country,
a.name s,
a.placetype,
b.ancestor_placetype,
b.ancestor_id,
a.latitude,
a.longitude,
a.min_latitude,
a.min_longitude,
a.max_latitude,
a.max_longitude,
a.is_current,
a.is_deprecated,
a.is_ceased,
a.is_superseded,
a.is_superseding,
a.superseded_by,
a.supersedes,
c.other_id,
c.other_source,
a.lastmodified,
d.body
from spr a
join names e on a.id = e.id
join ancestors b on a.id = b.id
join concordances c on a.id = c.id
join geojson d on a.id = d.id
where a.placetype in ('timezone')
group by a.id 
```
