# timezone_shapefiles

[https://traveladdicts.unli.xyz/guestblog/timezone-shapefiles](https://traveladdicts.unli.xyz/guestblog/timezone-shapefiles)

data extracted from [who's on first](https://github.com/whosonfirst-data/whosonfirst-data/blob/master/LICENSE.md)

```
select 
group_concat( e.name || ',') n,
a.id,
a.parent_id,
a.name s,
a.placetype,
a.country,
a.repo,
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
a.lastmodified,
b.id,
b.ancestor_id,
b.ancestor_placetype,
b.lastmodified,
c.id,
c.other_id,
c.other_source,
c.lastmodified,
d.id,
d.body,
d.lastmodified
from spr a
join names e on a.id = e.id
join ancestors b on a.id = b.id
join concordances c on a.id = c.id
join geojson d on a.id = d.id
where a.placetype in ('timezone')
group by a.id 
```
