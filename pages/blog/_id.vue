<template>
  <div class="home">
    <app-blog-heading />
    <div class="blog-details-area pt-100 pb-70">
      <div class="container">
        <div class="row">
          <div class="col-lg-8">
            <app-blog-body :blogDetails="blogDetails" />
          </div>
          <div class="col-lg-4">
            <app-blog-side-archive :blogDetails="blogDetails" />
            <app-blog-side-blogs :latestBlogs="latestBlogs" />
            <app-blog-side-tags :blogDetails="blogDetails" />
            <app-blog-gallery :blogDetails="blogDetails" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AppBlogBody from "../../components/blog/AppBlogBody.vue";
import AppBlogSideBlogs from "../../components/blog/AppBlogSideBlogs.vue";
import AppBlogHeading from "../../components/blog/AppBlogHeading.vue";
import AppBlogSideTags from "../../components/blog/AppBlogSideTags.vue";
import AppBlogGallery from "../../components/blog/AppBlogGallery.vue";
import AppBlogSideArchive from "../../components/blog/AppBlogSideArchive.vue";
export default {
  components: {
    AppBlogHeading,
    AppBlogBody,
    AppBlogSideBlogs,
    AppBlogSideTags,
    AppBlogGallery,
    AppBlogSideArchive,
  },
  async asyncData({ $axios, params, app }) {
    const BLOG_DETAILS = await $axios.get(`/blogs/${params.id}`, {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    const LATEST_BLOGS = await $axios.get(`/blogs/?latest=1`, {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    return {
      blogDetails: BLOG_DETAILS.data.data,
      latestBlogs: LATEST_BLOGS.data.data.blogs,
    };
  },
};
</script>

<style></style>
